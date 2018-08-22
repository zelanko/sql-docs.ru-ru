---
title: Подключение к SQL Server (DB2eToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: b59803cb-3cc6-41cc-8553-faf90851410e
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 5315b8f1b91d60d71ab1dd6d0c3b060e4fb82a48
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "40393038"
---
# <a name="connecting-to-sql-server-db2etosql"></a>Подключение к SQL Server (DB2eToSQL)
Для переноса баз данных DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014 или Azure SQL DB, необходимо подключиться к любой из этих экземпляров целевого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При подключении, SSMA получает метаданные обо всех базах данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и отображает метаданные базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных. SSMA хранит сведения о какой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вы подключены, но не хранит пароли.  
  
Подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] остается активным, пока не закрыть проект. При повторном открытии проекта, необходимо повторно подключить к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Если требуется активное подключение к серверу. Автономном время загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и перенос данных.  
  
Метаданные об экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически не синхронизирован. Вместо этого для обновления метаданных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных, необходимо вручную обновить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданных. Дополнительные сведения см. в разделе «синхронизация [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданных» ниже в этом разделе.  
  
## <a name="required-sql-server-permissions"></a>Разрешения требуется SQL Server  
Учетная запись, которая используется для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требует разных разрешений в зависимости от действий, выполняемых в учетной записи:  
  
-   Для преобразования объектов DB2 к [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис для обновления метаданных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или чтобы сохранить преобразованный синтаксис скриптов, она должна иметь разрешение на вход к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Для загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], учетная запись должна быть членом **sysadmin** роли сервера. Это необходимо для установки сборки среды CLR.  
  
-   Чтобы перенести данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], учетная запись должна быть членом **sysadmin** роли сервера. Это необходимо для запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пакетов для миграции данных агента.  
  
-   Чтобы запустить код, который формируется SSMA, учетная запись должна иметь **Execute** разрешения для всех определяемых пользователем функций в **ssma_DB2** схемы целевой базы данных. Эти функции предоставляют функциональные возможности, аналогичные функции системы DB2 и используемые преобразованных объектов.  
  
Если учетная запись, которая используется для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] — для переноса всех задач, учетная запись должна быть членом **sysadmin** роли сервера.  
  
## <a name="establishing-a-sql-server-connection"></a>Установки подключения к серверу SQL  
Перед началом преобразования объектов базы данных DB2 для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис, необходимо установить подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] место для переноса базы данных DB2 или баз данных.  
  
При определении свойств соединения, также указать базу данных, где объекты и данные будут перенесены. Это сопоставление на уровне схемы DB2 можно настроить, после подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [сопоставление схем DB2 со схемами SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md).  
  
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
  
    Этот параметр недоступен при повторном подключении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  В **проверки подлинности** выберите тип проверки подлинности, используемый для соединения. Чтобы использовать текущую учетную запись Windows, выберите **проверки подлинности Windows**. Для использования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имени входа, выберите **проверки подлинности SQL Server**, а затем укажите имя входа и пароль.  
  
6.  Для безопасного подключения, добавляются два элемента управления, **шифровать соединение** и **TrustServerCertificate** флажки. Только тогда, когда **шифровать соединение** установлен, **TrustServerCertificate** флажок становится видимым. Когда **шифровать соединение** проверяется (true) и **TrustServerCertificate** снят (false), он будет проверять сертификат SSL сервера SQL. Проверка сертификата сервера является частью SSL-подтверждения и гарантирует, что для подключения выбран правильный сервер. Чтобы обеспечить это, необходимо установить сертификат на стороне клиента, а также на стороне сервера.  
  
7.  Нажмите кнопку **Соединить**.  
  
**Выше версии совместимости**  
  
-   Вы сможете подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, при миграции проекта, созданного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005.  
  
-   Вы сможете подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, при миграции проекта, созданного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008, но вы не сможете подключиться к более ранние версии, т. е. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005.  
  
-   Вы сможете подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, если проект создан не SQL Server 2012.  
  
||||||  
|-|-|-|-|-|  
|**ВЕРСИЯ целевого сервера Vs тип проекта**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 <br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 <br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 <br />(Version:13.x)|База данных Azure SQL|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014||Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014|||Да||  
|База данных Azure SQL||||Да|  
  
> [!IMPORTANT]  
> Преобразование объектов базы данных выполняется в соответствии с типом проекта, но не в соответствии с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вы подключены. В частности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 г., [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 или Azure SQL DB.  
  
## <a name="synchronizing-sql-server-metadata"></a>Синхронизация метаданных SQL Server  
Метаданные о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных не обновляется автоматически. Метаданные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных представляет собой моментальный снимок метаданные при первом подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или последнего времени, когда вручную обновленных метаданных. Можно вручную обновить метаданные для всех баз данных или для любой отдельной базы данных или объект базы данных.  
  
**Чтобы синхронизировать метаданные**  
  
1.  Убедитесь, что вы подключены к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных, установите флажок рядом с базой данных или схемы, который вы хотите обновить базы данных.  
  
    Например, чтобы обновить метаданные для всех баз данных, установите в поле **баз данных**.  
  
3.  Щелкните правой кнопкой мыши **баз данных**, или отдельной базы данных или схему базы данных, а затем выберите **синхронизация с базой данных**.  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в процессе переноса зависит от требований проекта:  
  
-   Чтобы настроить сопоставление схем DB2 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных и схем, см. в разделе [сопоставление схем DB2 со схемами SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md).  
  
-   Чтобы настроить параметры конфигурации для проектов, см. в разделе [параметры проекта &#40;преобразования&#41; &#40;DB2ToSQL&#41; ](../../ssma/db2/project-settings-conversion-db2tosql.md) и связанных разделах.  
  
-   Чтобы настроить сопоставление исходной и целевой типы данных, см. в разделе [сопоставление DB2 и типов данных SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
-   Если у вас нет необходимости выполнять эти задачи, вы можете преобразовать определения объектов базы данных DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определений объекта. Дополнительные сведения см. в разделе [преобразование схем DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md).  
  
## <a name="see-also"></a>См. также  
[Миграция DB2 баз данных в SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
