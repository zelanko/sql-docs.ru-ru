---
title: Диспетчер подключений ADO.NET | Документы Майкрософт
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.adonetconnection.f1
helpviewer_keywords:
- connection managers [Integration Services], ADO.NET
- ADO.NET connection manager [Integration Services]
- connections [Integration Services], ADO.NET
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 32b01cce82cd1fd2af018b002a3c551ea480c000
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67897990"
---
# <a name="adonet-connection-manager"></a>Диспетчер соединений ADO.NET

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] позволяет пакету обращаться к источникам данных с помощью поставщика .NET. Чаще всего этот диспетчер используется для доступа к таким источникам данных, как [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также к источникам данных, предоставляемым посредством OLE DB и XML в пользовательских задачах, написанных на управляемом коде, например коде языка C#.  
  
 Если добавить к пакету диспетчер соединений служб [!INCLUDE[vstecado](../../includes/vstecado-md.md)] , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that is resolved as an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection at run time, sets the connection manager properties, and adds the connection manager to the **Connections** collection on the package.  
  
 Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **ADO.NET**. Значение **ConnectionManagerType** уточняется: в него включается имя поставщика .NET, используемого диспетчером соединений.  
  
## <a name="adonet-connection-manager-troubleshooting"></a>Устранение неполадок, связанных с диспетчером соединений ADO.NET  
 В журнал можно записывать вызовы, сделанные диспетчером соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] к внешним источникам данных. Эта возможность протоколирования может быть использована для устранения неполадок соединений, которые устанавливаются диспетчером соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] с внешними источниками данных. Чтобы протоколировать вызовы, которые диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] совершает к внешним поставщикам данных, необходимо разрешить ведение журнала пакета и выбрать событие **Диагностика** на уровне пакета. Дополнительные сведения см. в разделе [Инструменты устранения неполадок при выполнении пакетов](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
 При чтении данных диспетчером соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] данные определенных типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формируют результаты, показанные в следующей таблице.  
  
|Тип данных SQL Server|Результат|  
|--------------------------|------------|  
|**time**, **datetimeoffset**|Выполнение пакета завершается неудачей, если в пакете не используются параметризованные команды SQL. Чтобы применить параметризованные команды SQL, используйте в пакете задачу «Выполнение SQL». Дополнительные сведения см. в разделах [Задача "Выполнение SQL"](../../integration-services/control-flow/execute-sql-task.md) и [Параметры и коды возврата в задаче "Выполнение SQL"](https://msdn.microsoft.com/library/a3ca65e8-65cf-4272-9a81-765a706b8663).|  
|**datetime2**|Диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] отбрасывает миллисекунды.|  
  
> [!NOTE]  
>  Дополнительные сведения о типах данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их сопоставлении с типами данных [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] см. в разделе [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md) и [Типы данных службы Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="adonet-connection-manager-configuration"></a>Настройка диспетчера соединений ADO.NET  
 Диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] можно настроить следующими способами:  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
-   Предоставьте специальную строку подключения, настроенную таким образом, чтобы удовлетворить требования выбранного поставщика .NET.  
  
-   В зависимости от поставщика предоставьте имя источника данных, к которому производится подключение.  
  
-   Предоставьте безопасные учетные данные, соответствующие выбранному поставщику.  
  
-   Обозначает, будет ли соединение, созданное из диспетчера соединений, сохранено во время выполнения.  
  
 Многие параметры конфигурации диспетчера соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] зависят от используемого им поставщика .NET.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в одном из последующих разделов.  
  
-   [настройка диспетчера соединений ADO.NET](../../integration-services/connection-manager/configure-ado-net-connection-manager.md)  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="configure-adonet-connection-manager"></a>настройка диспетчера соединений ADO.NET
  Диалоговое окно **Настройка диспетчера соединений ADO.NET** используется для добавления соединения с источником данных, доступ к которому будет осуществляться с помощью поставщика данных .NET Framework, например поставщиком SqlClient. Диспетчер соединений использует существующее соединение, либо можно создать новое.  
  
 Дополнительные сведения о диспетчере соединений ADO.NET см. в разделе [ADO.NET Connection Manager](../../integration-services/connection-manager/ado-net-connection-manager.md).  
  
### <a name="options"></a>Параметры  
 **Подключения к данным**  
 Выберите из списка существующее подключение к данным ADO.NET.  
  
 **Свойства подключения к данным**  
 Просмотрите свойства и значения выбранного подключения к данным ADO.NET.  
  
 **Создать**  
 Создание подключения к данным ADO.NET с помощью диалогового окна **Диспетчер соединений** .  
  
 **Удаление**  
 Выберите соединение и затем удалите его, используя кнопку **Удалить** .  
  
### <a name="managed-identities-for-azure-resources-authentication"></a>Управляемые удостоверения для проверки подлинности ресурсов Azure
При выполнении пакетов SSIS в [среде Azure-SSIS Integration Runtime фабрики данных Azure](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime) вы можете использовать [управляемое удостоверение](https://docs.microsoft.com/azure/data-factory/connector-azure-sql-database#managed-identity), связанное с вашей фабрикой данных, для проверки подлинности базы данных SQL Azure (или управляемого экземпляра). С помощью этого удостоверения назначенная фабрика может обращаться к данным и копировать их из вашей базы данных или в нее.

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

1. **Предоставьте группе Azure AD необходимые разрешения**, как обычно делаете это для пользователей SQL и других лиц. Например, выполните следующий код:

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

1. **Предоставьте управляемому удостоверению фабрики данных необходимые разрешения**. Запустите следующий код T-SQL для базы данных, откуда или куда вы хотите скопировать данные:

    ```sql
    CREATE USER [{the managed identity name}] FOR LOGIN [{the managed identity name}] WITH DEFAULT_SCHEMA = dbo
    ALTER ROLE db_owner ADD MEMBER [{the managed identity name}]
    ```

Наконец, **настройте проверку подлинности управляемого удостоверения** для диспетчера подключений ADO.NET. Это можно сделать двумя способами.
    
1. Настройка во время разработки. В конструкторе SSIS щелкните диспетчер подключений ADO.NET правой кнопкой мыши и выберите **Свойства**, чтобы открыть **окно свойств**. Измените значение свойства **ConnectUsingManagedIdentity** на **True**.
    > [!NOTE]
    >  Сейчас свойство **ConnectUsingManagedIdentity** диспетчера подключений не оказывает никакого влияния (то есть проверка подлинности управляемого удостоверения не работает) при выполнении пакета SSIS в конструкторе SSIS или [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server.
    
1. Настройка во время выполнения. При выполнении пакета с помощью [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/integration-services/ssis-quickstart-run-ssms) или [действия "Выполнить пакет SSIS" Фабрики данных Azure ](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity) найдите диспетчер подключений ADO.NET и измените значение его свойства **ConnectUsingManagedIdentity** на **True**.
    > [!NOTE]
    >  В среде Azure-SSIS Integration Runtime все остальные методы проверки подлинности (например, встроенная проверка подлинности, пароль), предварительно настроенные в диспетчере подключений ADO.NET, будут **переопределены**, когда для установки подключения к базе данных используется проверка подлинности управляемого удостоверения.

> [!NOTE]
>  Чтобы настроить проверку подлинности управляемого удостоверения для существующих пакетов, нужно хотя бы раз перестроить проект SSIS с использованием [последнего конструктора SSIS](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) и повторного развернуть этот проект в Azure-SSIS Integration Runtime, чтобы новое свойство диспетчера подключений **ConnectUsingManagedIdentity** автоматически добавлялось во все диспетчеры подключений ADO.NET в проекте SSIS.

## <a name="see-also"></a>См. также:  
 [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
