---
title: Создание учетной записи-посредника агента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 05/04/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], creating
ms.assetid: 142e0c55-a8b9-4669-be49-b9dc602d5988
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 452cec6a4cfcf5f1f85a4e05f6522007851a31ca
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65095531"
---
# <a name="create-a-sql-server-agent-proxy"></a>Создание учетной записи-посредника агента SQL Server
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описано, как создать учетную запись-посредник агента SQL Server в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
Учетная запись-посредник агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет контекст безопасности, в котором может выполняться шаг задания. Каждой учетной записи-посреднику соответствует учетная запись системы безопасности. Чтобы установить разрешения для определенного шага задания, создайте учетную запись-посредник, которая имеет необходимые разрешения для подсистемы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и затем назначьте эту учетную запись-посредник шагу задания.  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   **Создание учетной записи-посредника агента SQL Server с помощью:**  
  
    [Среда SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   Перед созданием учетной записи-посредника необходимо создать учетные данные, если они еще не созданы.  
  
-   Учетные записи-посредники агента[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используют учетные данные для хранения сведений об учетных записях пользователей Windows. Пользователь, указанный в учетных данных, должен иметь разрешение "Доступ к этому компьютеру из сети" (SeNetworkLogonRight) на компьютере, где выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверяет действительность доступа к подсистеме учетной записи-посредника и предоставляет ей доступ при каждом выполнении шага задания. Если учетная запись-посредник больше не имеет доступа к подсистеме, шаг задания завершается ошибкой. В противном случае агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] олицетворяет пользователя, указанного в учетной записи-посреднике, и запускает шаг задания.  
  
-   Создание учетной записи-посредника не влияет на разрешения пользователя, указанного в учетных данных учетной записи-посредника. Например, можно создать учетную запись-посредник для пользователя, не имеющего разрешения на подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В этом случае шаги задания, использующие эту учетную запись-посредник, не смогут соединяться с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Если имени входа пользователя предоставлен доступ к учетной записи-посреднику или пользователь принадлежит к любой роли с доступом к учетной записи-посреднику, то он может использовать учетную запись-посредник в шаге задания.  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
  
-   Только члены предопределенной роли сервера **sysadmin** имеют разрешение на создание, изменение или удаление учетных записей-посредников. Пользователи, не являющиеся членами предопределенной роли сервера **sysadmin**, должны быть добавлены к одной из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb**, чтобы использовать записи-посредники: **SQLAgentUserRole**, **SQLAgentReaderRole** или **SQLAgentOperatorRole**.  
  
-   При создании учетных данных в дополнение к учетной записи-посреднику требуется разрешение **ALTER ANY CREDENTIAL** .  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a>Создание учетной записи-посредника агента SQL Server  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, на котором необходимо создать учетную запись-посредник агента SQL Server.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши папку **Прокси-серверы** и выберите пункт **Создать прокси-сервер**.  
  
4.  В диалоговом окне **Создание учетной записи-посредника** на странице **Общие** введите имя учетной записи-посредника в поле **Имя учетной записи-посредника** .  
  
5.  В поле **Учетные данные** введите учетные данные, которые будут использоваться учетной записью-посредником.  
  
6.  В поле **Описание** введите описание учетной записи-посредника.  
  
7.  В поле **Активна для следующих подсистем**выберите соответствующую подсистему или подсистемы для этой учетной записи-посредника.  
  
8.  На вкладке **Участники** добавьте или удалите имена входа или роли, чтобы предоставить или отменить доступ к учетной записи-посреднику.  
  
9. После завершения нажмите кнопку **ОК**.  
  
## <a name="TsqlProcedure"></a>Использование Transact-SQL  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a>Создание учетной записи-посредника агента SQL Server  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- creates credential CatalogApplicationCredential  
    USE msdb ;  
    GO  
    CREATE CREDENTIAL CatalogApplicationCredential WITH IDENTITY = 'REDMOND/TestUser',   
        SECRET = 'G3$1o)lkJ8HNd!';  
    GO  
    -- creates proxy "Catalog application proxy" and assigns
    -- the credential 'CatalogApplicationCredential' to it.  
    EXEC dbo.sp_add_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 1,  
        @description = 'Maintenance tasks on catalog application.',  
        @credential_name = 'CatalogApplicationCredential' ;  
    GO  
    -- grants the proxy "Catalog application proxy" access to 
    -- the ActiveX Scripting subsystem.  
    EXEC dbo.sp_grant_proxy_to_subsystem  
        @proxy_name = N'Catalog application proxy',  
        @subsystem_id = 2 ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе:  
  
-   [CREATE CREDENTIAL (Transact-SQL)](https://msdn.microsoft.com/d5e9ae69-41d9-4e46-b13d-404b88a32d9d)  
  
-   [Хранимая процедура sp_add_proxy (Transact-SQL)](https://msdn.microsoft.com/cb59df37-f103-439b-bec1-2871fb669a8b)  
  
-   [sp_grant_proxy_to_subsystem (Transact-SQL)](https://msdn.microsoft.com/866aaa27-a1e0-453a-9b1b-af39431ad9c2)  
  
