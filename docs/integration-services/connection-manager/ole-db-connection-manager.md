---
title: Диспетчер подключений OLE DB | Документы Майкрософт
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.oledbconnection.f1
helpviewer_keywords:
- OLE DB connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], OLE DB
- connections [Integration Services], OLE DB
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
author: janinezhang
ms.author: janinez
ms.openlocfilehash: d3b1526d55321e5f32a243a48f64bde2f579caa6
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028794"
---
# <a name="ole-db-connection-manager"></a>диспетчер соединений OLE DB

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Диспетчер соединений OLE DB позволяет пакету подключаться к источнику данных с помощью поставщика OLE DB. Например, диспетчер соединений OLE DB, который подключается к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , может использовать поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].    
    
> [!NOTE]
>  Собственный поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 11.0 не поддерживает новые ключевые слова строки соединения (MultiSubnetFailover=True) для отказоустойчивых кластеров с несколькими подсетями. Дополнительные сведения см. в разделе [Заметки о выпуске SQL Server](https://go.microsoft.com/fwlink/?LinkId=247824) и запись блога [Always On Multi-Subnet Failover and SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/)(Отработка отказа в нескольких подсетях и службы SSIS) на сайте www.mattmasson.com.    
> 
> [!NOTE]
>  Если источником данных является [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007 или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007, то для него понадобится источник данных, отличный от поставщиков для более ранних версий Excel или Access. Дополнительные сведения см. в разделе [Подключение к книге Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md) и [Подключение к базе данных Access](../../integration-services/connection-manager/connect-to-an-access-database.md).    
    
 Некоторые задачи служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и компоненты потока данных применяют диспетчер соединений OLE DB. Например, источник OLE DB и назначение «OLE DB» применяют диспетчер соединений для извлечения и загрузки данных, а задача «Выполнение SQL» может применять его для подключения к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы выполнять запросы.    
    
 Кроме того, диспетчер соединений OLE DB применяется для доступа к источникам данных OLE DB в пользовательских задачах, написанных неуправляемым кодом на языке, подобном C++.    
    
 При добавлении к пакету диспетчера соединений OLE DB службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер соединений, который будет решать задачи соединений OLE DB во время выполнения, устанавливает свойства диспетчера соединений и добавляет его к коллекции **Connections** пакета.    
    
 Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **OLEDB**.    
    
 Диспетчер соединений OLE DB можно настроить следующими способами:    
    
-   Укажите конкретную строку соединения, соответствующую требованиям конфигурации выбранного поставщика.    
    
-   В зависимости от поставщика предоставьте имя источника данных, к которому производится подключение.    
    
-   Предоставьте безопасные учетные данные, соответствующие выбранному поставщику.    
    
-   Обозначает, будет ли соединение, созданное из диспетчера соединений, сохранено во время выполнения.    
    
## <a name="logging"></a>Ведение журнала    
 В журнал можно записывать вызовы, сделанные диспетчером соединений OLE DB к внешним поставщикам данных. Эта возможность ведения журнала может быть использована для устранения неполадок соединений, которые выполняются диспетчером соединений OLE DB к внешним источникам данных. Чтобы вести журнал вызовов, которые диспетчер соединений OLE DB совершает к внешним поставщикам данных, необходимо включить ведение журнала пакета и выбрать событие **Диагностика** на уровне пакета. Дополнительные сведения см. в разделе [Инструменты устранения неполадок при выполнении пакетов](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).    
    
## <a name="configuration-of-the-oledb-connection-manager"></a>Настройка диспетчера соединений OLE DB    
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами. Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в разделе [Настройка диспетчера соединений OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md). Дополнительные сведения о настройке диспетчера соединений программными средствами см. в документации по классу **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** в руководстве для разработчиков.    
    
## <a name="related-content"></a>См. также    
    
-   Статья Wiki [Соединители служб SSIS с Oracle](https://go.microsoft.com/fwlink/?LinkId=220670) на сайте social.technet.microsoft.com    
    
-   Техническая статья [Connection Strings for OLE DB Providers](https://go.microsoft.com/fwlink/?LinkId=220744)(Строки подключения для поставщиков OLE DB) на сайте carlprothman.net.    
    
## <a name="configure-ole-db-connection-manager"></a>настройка диспетчера соединений OLE DB
  Используйте диалоговое окно **Настройка диспетчера соединений OLE DB** , чтобы добавить соединение с источником данных. Это может быть либо новое соединение, либо копия существующего соединения.  
  
> [!NOTE]  
>  Для источника данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007 потребуется поставщик данных, отличный от того, который использовался в предыдущих версиях Excel. Дополнительные сведения см. в разделе [Подключение к книге Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md).  
>   
>  Если источником данных является [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007, то для него понадобится поставщик OLE DB, отличающийся от поставщиков для более ранних версий Access. Дополнительные сведения см. в разделе [Подключение к базе данных Access](../../integration-services/connection-manager/connect-to-an-access-database.md).  
  
 Дополнительные сведения о диспетчере соединений OLE DB см. в разделе [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
### <a name="options"></a>Параметры  
 **Подключения к данным**  
 Выберите из списка существующее подключение к данным OLE DB.  
  
 **Свойства подключения к данным**  
 Просмотрите свойства и значения выбранного подключения к данным OLE DB.  
  
 **Создать**  
 Создайте подключение к данным OLE DB с помощью диалогового окна **Диспетчер соединений** .  
  
 **Удаление**  
 Выберите подключение к данным и удалите его с помощью кнопки **Удалить** .  
  
### <a name="managed-identities-for-azure-resources-authentication"></a>Управляемые удостоверения для проверки подлинности ресурсов Azure
При выполнении пакетов SSIS в [среде Azure-SSIS Integration Runtime фабрики данных Azure](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime) вы можете использовать [управляемое удостоверение](https://docs.microsoft.com/azure/data-factory/connector-azure-sql-database#managed-identity), связанное с вашей фабрикой данных, для проверки подлинности базы данных SQL Azure (или управляемого экземпляра). С помощью этого удостоверения назначенная фабрика может обращаться к данным и копировать их из вашей базы данных или в нее.

> [!NOTE]
>  При использовании проверки подлинности Azure AD (включая проверку подлинности с помощью управляемого удостоверения) для подключения к Базе данных SQL Azure (или к управляемому экземпляру) возникают известные проблемы, которые могут привести к сбою при выполнении пакета или непредвиденному изменению в поведении. Дополнительные сведения см. в разделе о [функциях и ограничениях Azure AD](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication#azure-ad-features-and-limitations).

Чтобы использовать проверку подлинности управляемого удостоверения для базы данных SQL Azure, выполните следующие действия для настройки базы данных:

1. **Создайте группу в Azure AD**. Сделайте управляемое удостоверение членом группы.
    
   1. [Найдите управляемое удостоверение фабрики данных на портале Microsoft Azure](https://docs.microsoft.com/azure/data-factory/data-factory-service-identity). Перейдите к разделу **Свойства** своей фабрики данных. Скопируйте **идентификатор объекта управляемого удостоверения**.
    
   1. Установите модуль [Azure AD PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2). Войдите с помощью команды `Connect-AzureAD`. Выполните указанные ниже команды, чтобы создать группу и добавить управляемое удостоверение в качестве члена.
      ```powershell
      $Group = New-AzureADGroup -DisplayName "<your group name>" -MailEnabled $false -SecurityEnabled $true -MailNickName "NotSet"
      Add-AzureAdGroupMember -ObjectId $Group.ObjectId -RefObjectId "<your data factory managed identity object ID>"
      ```
    
1. **[Подготовьте администратора Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#provision-an-azure-active-directory-administrator-for-your-azure-sql-database-server)** для своего сервера SQL Azure на портале Microsoft Azure, если вы еще этого не сделали. Администратор Azure AD может быть пользователем Azure AD или группой Azure AD. Если вы предоставляете группе с управляемым удостоверением роль администратора, пропустите шаги 3 и 4. Администратор будет иметь полный доступ к базе данных.

1. **[Создайте пользователей автономной базы данных](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#create-contained-database-users-in-your-database-mapped-to-azure-ad-identities)** для группы Azure AD. Подключитесь к базе данных, откуда или куда вы хотите скопировать данные с помощью таких средств, как SSMS, с используя удостоверение Azure AD, которое имеет по меньшей мере разрешение ALTER ANY USER. Выполните следующий код T-SQL: 
    
    ```sql
    CREATE USER [your AAD group name] FROM EXTERNAL PROVIDER;
    ```

1. **Предоставьте группе Azure AD необходимые разрешения**, как обычно делаете это для пользователей SQL и других лиц. Сведения о соответствующих ролях см. в статье [Роли уровня базы данных](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles).  Например, выполните следующий код:

    ```sql
    ALTER ROLE [role name] ADD MEMBER [your AAD group name];
    ```

Чтобы использовать проверку подлинности управляемого удостоверения для Управляемого экземпляра базы данных SQL Azure, выполните следующие действия для настройки базы данных:
    
1. **[Подготовьте администратора Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#provision-an-azure-active-directory-administrator-for-your-managed-instance)** для своего управляемого экземпляра на портале Microsoft Azure, если вы еще этого не сделали. Администратор Azure AD может быть пользователем Azure AD или группой Azure AD. Если вы предоставляете группе с управляемым удостоверением роль администратора, пропустите шаги 2–5. Администратор будет иметь полный доступ к базе данных.

1. **[Найдите управляемое удостоверение фабрики данных на портале Microsoft Azure](https://docs.microsoft.com/azure/data-factory/data-factory-service-identity)** . Перейдите к разделу **Свойства** своей фабрики данных. Скопируйте **идентификатор приложения управляемого удостоверения** (не **идентификатор объекта управляемого удостоверения**).

1. **Преобразуйте управляемое удостоверение фабрики данных в двоичный тип**. Подключитесь к базе данных **master** в своем управляемом экземпляре с помощью таких средств, как SSMS, используя свою учетную запись администратора SQL/Active Directory. Выполните следующий код T-SQL для базы данных **master**, чтобы получить идентификатор приложения управляемого удостоверения в двоичном формате:
    
    ```sql
    DECLARE @applicationId uniqueidentifier = '{your managed identity application ID}'
    select CAST(@applicationId AS varbinary)
    ```

1. **Добавьте управляемое удостоверение фабрики данных в качестве пользователя** в Управляемый экземпляр базы данных SQL Azure. Запустите следующий код T-SQL для базы данных **master**:
    
    ```sql
    CREATE LOGIN [{a name for the managed identity}] FROM EXTERNAL PROVIDER with SID = {your managed identity application ID as binary}, TYPE = E
    ```

1. **Предоставьте управляемому удостоверению фабрики данных необходимые разрешения**. Сведения о соответствующих ролях см. в статье [Роли уровня базы данных](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles). Запустите следующий код T-SQL для базы данных, откуда или куда вы хотите скопировать данные:

    ```sql
    CREATE USER [{the managed identity name}] FOR LOGIN [{the managed identity name}] WITH DEFAULT_SCHEMA = dbo
    ALTER ROLE [role name] ADD MEMBER [{the managed identity name}]
    ```

Затем **настройте поставщик OLE DB** для диспетчера подключений OLE DB. Это можно сделать двумя способами.
    
1. Настройка во время разработки. В конструкторе SSIS дважды щелкните диспетчер подключений OLE DB, чтобы открыть окно **Диспетчер подключений**. В раскрывающемся списке **Поставщик** выберите [**Microsoft OLE DB Driver for SQL Server**](https://go.microsoft.com/fwlink/?linkid=871294).
    > [!NOTE]
    >  Другие поставщики в раскрывающемся списке могут не поддерживать проверку подлинности управляемого удостоверения.
    
1. Настройка во время выполнения. При выполнении пакета с помощью [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/integration-services/ssis-quickstart-run-ssms) или [действия "Выполнить пакет SSIS" фабрики данных Azure ](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity) найдите свойство **ConnectionString** для диспетчера подключений OLE DB и измените значение свойства подключения **Provider** на **MSOLEDBSQL** (например, Microsoft OLE DB Driver for SQL Server).
    ```vb
    Data Source=serverName;Initial Catalog=databaseName;Provider=MSOLEDBSQL;...
    ```

Наконец, **настройте проверку подлинности управляемого удостоверения** для диспетчера подключений OLE DB. Это можно сделать двумя способами.
    
1. Настройка во время разработки. В конструкторе SSIS щелкните диспетчер подключений OLE DB правой кнопкой мыши и выберите **Свойства**, чтобы открыть **окно свойств**. Измените значение свойства **ConnectUsingManagedIdentity** на **True**.
    > [!NOTE]
    >  Сейчас свойство **ConnectUsingManagedIdentity** диспетчера подключений не оказывает никакого влияния (то есть проверка подлинности управляемого удостоверения не работает) при выполнении пакета SSIS в конструкторе SSIS или [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server.

1. Настройка во время выполнения. При выполнении пакета с помощью SSMS или действия "Выполнить пакет SQL" найдите диспетчер подключений OLE DB и измените значение его свойства **ConnectUsingManagedIdentity** на **True**.
    > [!NOTE]
    >  В среде Azure-SSIS Integration Runtime все остальные методы проверки подлинности (например, встроенная система безопасности, пароль), предварительно настроенные в диспетчере подключений OLE DB, будут **переопределены**, когда для установки подключения к базе данных используется проверка подлинности управляемого удостоверения.

> [!NOTE]
>  Чтобы настроить проверку подлинности с помощью управляемого удостоверения для существующих пакетов, рекомендуется хотя бы раз перестроить проект SSIS с использованием [последнего конструктора SSIS](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) и повторно развернуть этот проект в среде выполнения интеграции Azure-SSIS, чтобы новое свойство диспетчера подключений **ConnectUsingManagedIdentity** автоматически добавлялось во все диспетчеры подключений OLE DB в проекте SSIS. Альтернативный способ — напрямую использовать переопределение свойства, указав при выполнении путь к свойству **\Package.Connections[{имя_диспетчера_подключений}].Properties[ConnectUsingManagedIdentity]**

## <a name="see-also"></a>См. также:    
 [Источник OLE DB](../../integration-services/data-flow/ole-db-source.md)     
 [Назначение «OLE DB»](../../integration-services/data-flow/ole-db-destination.md)     
 [Задача «Выполнение SQL»](../../integration-services/control-flow/execute-sql-task.md)     
 [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md)    
    
  
