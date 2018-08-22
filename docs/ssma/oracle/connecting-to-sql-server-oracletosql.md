---
title: Подключение к SQL Server (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Connecting to SQL Server,Synchronizing SQL Server Metadata
ms.assetid: 1b2a8059-1829-4904-a82f-9c06de1e245f
caps.latest.revision: 16
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 3360da5567d1ff1efef7cbac8e235bc508bef3bb
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "40392584"
---
# <a name="connecting-to-sql-server-oracletosql"></a>Подключение к SQL Server (OracleToSQL)
Для переноса баз данных Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014, необходимо подключиться к любой из этих целевых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При подключении, SSMA получает метаданные обо всех базах данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и отображает метаданные базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных. SSMA хранит сведения о какой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вы подключены, но не хранит пароли.  
  
Подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] остается активным, пока не закрыть проект. При повторном открытии проекта, необходимо повторно подключить к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Если требуется активное подключение к серверу. Автономном время загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и перенос данных.  
  
Метаданные об экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически не синхронизирован. Вместо этого для обновления метаданных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных, необходимо вручную обновить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданных. Дополнительные сведения см. в разделе «синхронизация [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданных» ниже в этом разделе.  
  
## <a name="required-sql-server-permissions"></a>Разрешения требуется SQL Server  
Учетная запись, которая используется для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требует разных разрешений в зависимости от действий, выполняемых в учетной записи:  
  
-   Для преобразования объектов Oracle для [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис для обновления метаданных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или чтобы сохранить преобразованный синтаксис скриптов, она должна иметь разрешение на вход к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Для загрузки объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], учетная запись должна быть членом **sysadmin** роли сервера. Это необходимо для установки сборки среды CLR.  
  
-   Чтобы перенести данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], учетная запись должна быть членом **sysadmin** роли сервера. Это необходимо для запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пакетов для миграции данных агента.  
  
-   Чтобы запустить код, который формируется SSMA, учетная запись должна иметь **Execute** разрешения для всех определяемых пользователем функций в **ssma_oracle** схемы целевой базы данных. Эти функции предоставляют функциональные возможности, аналогичные функции системы Oracle и используемые преобразованных объектов.  
  
Если учетная запись, которая используется для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] — для переноса всех задач, учетная запись должна быть членом **sysadmin** роли сервера.  
  
## <a name="establishing-a-sql-server-connection"></a>Установки подключения к серверу SQL  
Перед началом преобразования объектов базы данных Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис, необходимо установить подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] место для переноса базы данных Oracle или базы данных.  
  
При определении свойств соединения, также указать базу данных, где объекты и данные будут перенесены. Вы это сопоставление можно настроить на уровне схемы Oracle после подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [сопоставление схем Oracle со схемами SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md).  
  
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
  
||||||||  
|-|-|-|-|-|-|-|  
|**ВЕРСИЯ целевого сервера Vs тип проекта**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005<br /> (Версия: 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008<br /> (Версия: 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 <br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 <br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 <br />(Version:13.x)|База данных Azure SQL|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|Да|Да|Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||Да|Да|Да|Да||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||Да|Да|Да||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014||||Да|Да||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016|||||Да||
|База данных Azure SQL||||||Да|
  
> [!IMPORTANT]  
> Преобразование объектов базы данных выполняется в соответствии с типом проекта, но не в соответствии с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вы подключены. Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 проекта преобразования выполняется согласно [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] несмотря на то, что вы подключены к более поздней версии 2005 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016).  
  
## <a name="synchronizing-sql-server-metadata"></a>Синхронизация метаданных SQL Server  
Метаданные о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных не обновляется автоматически. Метаданные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных представляет собой моментальный снимок метаданные при первом подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или последнего времени, когда вручную обновленных метаданных. Можно вручную обновить метаданные для всех баз данных или для любой отдельной базы данных или объект базы данных.  
  
**Чтобы синхронизировать метаданные**  
  
1.  Убедитесь, что вы подключены к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных, установите флажок рядом с базой данных или схемы, который вы хотите обновить базы данных.  
  
    Например, чтобы обновить метаданные для всех баз данных, установите в поле **баз данных**.  
  
3.  Щелкните правой кнопкой мыши **баз данных**, или отдельной базы данных или схему базы данных, а затем выберите **синхронизация с базой данных**.  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в процессе переноса зависит от требований проекта:  
  
-   Чтобы настроить сопоставление схем Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных и схем, см. в разделе [сопоставление схем Oracle со схемами SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md).  
  
-   Чтобы настроить параметры конфигурации для проектов, см. в разделе [Настройка параметров проекта &#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md).  
  
-   Чтобы настроить сопоставление исходной и целевой типы данных, см. в разделе [сопоставление Oracle и типы данных SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
-   Если у вас нет необходимости выполнять эти задачи, вы можете преобразовать определения объектов базы данных Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определений объекта. Дополнительные сведения см. в разделе [преобразование схем Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md).  
  
## <a name="see-also"></a>См. также  
[Переход с Oracle баз данных в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
