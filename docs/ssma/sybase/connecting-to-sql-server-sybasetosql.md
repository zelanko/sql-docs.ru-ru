---
title: Подключение к SQL Server (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to SQL Server
ms.assetid: dd368a1a-45b0-40e9-b4d3-5cdb48c26606
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: c5624c0b0fc298c3e303ee3ed7572da44e8a44c0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682012"
---
# <a name="connecting-to-sql-server-sybasetosql"></a>Подключение к SQL Server (SybaseToSQL)
Для переноса баз данных Sybase Adaptive Server Enterprise (ASE) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо подключиться к любому из экземпляров целевого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При подключении, SSMA получает метаданные обо всех базах данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и отображает метаданные базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных. SSMA хранит сведения о какой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вы подключены, но не хранит пароли.  
  
Подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] остается активным, пока не закрыть проект. При повторном открытии проекта, необходимо повторно подключить к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Если требуется активное подключение к серверу. Автономном время загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и перенос данных.  
  
Метаданные об экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически не синхронизирован. Вместо этого Если вы хотите обновлять метаданные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных, необходимо вручную обновить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданных, как описано в разделе «Synchronizing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданных» подразделе данного раздела.  
  
## <a name="required-sql-server-permissions"></a>Разрешения требуется SQL Server  
Учетная запись, которая используется для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требует разных разрешений в зависимости от действия, выполняемые с этой учетной записи.  
  
-   Для преобразования объектов ASE для [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис для обновления метаданных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или чтобы сохранить преобразованный синтаксис скриптов, она должна иметь разрешение на вход в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Для загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], требование минимально необходимым разрешением является членство в **db_owner** роли базы данных в целевую базу данных.  
  
-   Чтобы перенести данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], учетная запись должна быть членом **sysadmin** роли сервера. Это необходимо для запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пакетов для миграции данных агента.  
  
-   Чтобы запустить код, который формируется SSMA, учетная запись должна иметь **Execute** разрешения для всех определяемых пользователем функций в **ssma_syb** схему **sysdb** базы данных. Эти функции предоставляют функциональные возможности, аналогичные функции системы ASE и используемые преобразованных объектов.  
  
Если учетная запись, которая используется для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] — для переноса всех задач, учетная запись должна быть членом **sysadmin** роли сервера.  
  
## <a name="establishing-a-sql-server-connection"></a>Установки подключения к серверу SQL  
Перед началом преобразования объектов базы данных ASE для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис, необходимо установить подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] которых необходимо выполнить миграцию ASE или баз данных.  
  
При определении свойств соединения, также указать базу данных, где объекты и данные будут перенесены. Это сопоставление на уровне схемы ASE можно настроить, после подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [сопоставление схем Sybase ASE со схемами SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).  
  
> [!IMPORTANT]  
> Прежде чем пытаться подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], убедитесь, что экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает и может принимать подключения.  
  
**Для подключения к SQL Server**  
  
1.  На **файл** меню, выберите **подключение к SQL Server**.  
  
    Если вы ранее подключались к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], команда будет называться **повторно подключиться к SQL Server**.  
  
2.  В диалоговом окне подключения введите или выберите имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Если вы подключаетесь к экземпляру по умолчанию на локальном компьютере, можно ввести **localhost** или точку (**.**).  
  
    -   Если вы подключаетесь к экземпляру по умолчанию на другом компьютере, введите имя компьютера.  
  
    -   Если вы подключаетесь к именованному экземпляру на другом компьютере, введите имя компьютера, следуют обратную косую черту и имя экземпляра, например Сервер\экземпляр.  
  
3.  Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен на прием подключений через нестандартный порт, введите номер порта, который используется для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключений в **порт сервера** поле. Для экземпляра по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], номер порта по умолчанию — 1433. Для именованных экземпляров SSMA будет пытаться получить номер порта из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы браузера.  
  
4.  В **базы данных** введите имя целевой базы данных.  
  
    Этот параметр недоступен при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  В **проверки подлинности** выберите тип проверки подлинности, используемый для соединения. Чтобы использовать текущую учетную запись Windows, выберите **проверки подлинности Windows**. Чтобы использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имени входа, выберите **проверки подлинности SQL Server** и укажите имя для входа и пароль.  
  
6.  Для безопасного подключения, добавляются два элемента управления, **шифровать соединение** и **TrustServerCertificate** флажки. Только тогда, когда **шифровать соединение** установлен, **TrustServerCertificate** флажок становится видимым. Когда **шифровать соединение** проверяется (true) и **TrustServerCertificate** снят (false), он будет проверять сертификат SSL сервера SQL. Проверка сертификата сервера является частью SSL-подтверждения и гарантирует, что для подключения выбран правильный сервер. Чтобы обеспечить это, необходимо установить сертификат на стороне клиента, а также на стороне сервера.  
  
7.  Нажмите кнопку **Соединить**.  
  
**Выше версии совместимости**  
  
-   Вы сможете подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, при миграции проекта, созданного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005.  
  
-   Вы сможете подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, при миграции проекта, созданного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008, но вы не сможете подключиться к более ранние версии, т. е. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005.  
  
-   Можно подключиться только к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, если проект создан не SQL Server 2012.  
  
-   Выше совместимость версий не является допустимым для SQL Azure.  
  
||||||||
|-|-|-|-|-|-|-|
|**ВЕРСИЯ целевого сервера Vs тип проекта**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005<br /> (Версия: 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008<br /> (Версия: 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 <br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 <br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 <br />(Version:13.x)|SQL Azure|
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|Да|Да|Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||Да|Да|Да|Да||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014||||Да|Да|| 
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016|||||Да||  
|SQL Azure||||||Да|  
  
> [!IMPORTANT]  
> Преобразование объектов базы данных выполняется в соответствии с типом проекта, но не в соответствии с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вы подключены. Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 проекта преобразования выполняется согласно [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] несмотря на то, что вы подключены к более поздней версии 2005 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016)  
  
## <a name="reconnecting-to-sql-server"></a>Повторное подключение к SQL Server  
Подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] остается активным, пока не закрыть проект. При повторном открытии проекта, необходимо повторно подключить к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Если требуется активное подключение к серверу. Можно работать вне сети до обновления метаданных, загрузка объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и перенести данные.  
  
Процедура при повторном подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] совпадает со значением процедуры для установления соединения.  
  
## <a name="synchronizing-sql-server-metadata"></a>Синхронизация метаданных SQL Server  
Метаданные о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных не обновляется автоматически. Метаданные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных представляет собой моментальный снимок метаданные при первом подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или последнего времени, когда вручную обновленных метаданных. Можно вручную обновить метаданные для всех баз данных или для любой отдельной базы данных или объект базы данных.  
  
**Чтобы синхронизировать метаданные**  
  
1.  Убедитесь, что вы подключены к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных, установите флажок рядом с базой данных или схемы, который вы хотите обновить базы данных.  
  
    Например, чтобы обновить метаданные для всех баз данных, установите в поле **баз данных**.  
  
3.  Щелкните правой кнопкой мыши баз данных или отдельной базы данных или схему базы данных, а затем выберите **синхронизация с базой данных**.  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в процессе переноса зависит от требований проекта:  
  
-   Если вы хотите настроить сопоставление между ASE баз данных и схем и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных и схем, см. в разделе [схем Sybase ASE, сопоставления, со схемами SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).  
  
-   Если вы хотите настроить параметры конфигурации для проектов, см. в разделе [Настройка параметров проекта &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md).  
  
-   Если требуется пользовательское сопоставление исходной и целевой типы данных, см. в разделе [сопоставление Sybase ASE и типы данных SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
-   Если не нужно выполнять какие-либо из них, вы можете преобразовать определения объектов базы данных Sybase ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определений объекта. Дополнительные сведения см. в разделе [преобразование объектов базы данных Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных Sybase ASE в SQL Server — база данных Azure SQL &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
