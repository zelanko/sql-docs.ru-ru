---
title: Создание целевого сервера | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ag.tsxwiz.complete.f1
- sql13.ag.tsxwiz.cover.f1
- sql13.ag.tsxwiz.credentials.f1
- sql13.ag.tsxwiz.msx.f1
helpviewer_keywords:
- Target Server Wizard
- SQL Server Agent jobs, target servers
- target servers [SQL Server], creating
ms.assetid: 13aabe2d-67fe-4c67-8d49-2928dd705b7a
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4cc7e47c66ca94389bc7430d48cf05a47631cfa8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33044441"
---
# <a name="make-a-target-server"></a>Создание целевого сервера
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описывается создание целевого сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)]или управляющих объектов SQL Server (SMO).  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [безопасность](#Security)  
  
-   **Для создания целевого сервера используется:**  
  
    [Среда SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
Распределенные задания, имеющие связанные с учетной записью-посредником шаги, выполняются в контексте учетной записи-посредника на целевом сервере. Убедитесь в том, что выполняются нижеприведенные условия, либо в том, что шаги заданий, связанные с учетной записью-посредником, не будут загружаться с главного сервера на целевой:  
  
-   Подраздел реестра главного сервера **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<&#42;имя_экземпляра&#42;>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) имеет значение 1 (true). По умолчанию для него задается значение 0 (false).  
  
-   На целевом сервере есть учетная запись-посредник. Ее имя совпадает с именем учетной записи-посредника на главном сервере, под которой выполняется шаг задания.  
  
Если шаги задания, использующие учетную запись-посредник, завершаются с ошибками при скачивании с главного сервера на целевой, то в столбце **error_message** в таблице **sysdownloadlist** базы данных **msdb** появятся следующие сообщения об ошибках:  
  
-   «Для этого шага задания необходима учетная запись-посредник, однако проверка совпадения учетной записи-посредника на целевом сервере отключена.»  
  
    Чтобы устранить эту ошибку, задайте для раздела реестра **AllowDownloadedJobsToMatchProxyName** значение 1.  
  
-   «Учетная запись-посредник не найдена.»  
  
    Чтобы устранить эту ошибку, убедитесь, что на целевом сервере есть учетная запись-посредник, имя которой совпадает с именем посреднической учетной записи на главном сервере, под которой выполняется шаг задания.  
  
#### <a name="Permissions"></a>Permissions  
По умолчанию разрешения на выполнение этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-make-a-target-server"></a>Создание целевого сервера  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните узел этого экземпляра.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**, укажите **Администрирование нескольких серверов**и выберите пункт **Сделать целевым**. **Мастер целевого сервера** проведет через процесс создания целевого сервера.  
  
3.  На странице **Выбор главного сервера** выберите главный сервер, от которого данный целевой сервер будет получать задания.  
  
    **Выбрать сервер**  
    Подключиться к главному серверу.  
  
    **Описание этого сервера**  
    Введите описание для данного целевого сервера. Целевой сервер выгрузит это описание на главный сервер.  
  
4.  На странице **Учетные данные для входа на главный сервер** создайте новое имя входа на целевой сервер, если это необходимо.  
  
    **Создать новое имя входа (если необходимо) и присвоить ему права на главный сервер**  
    Если указанное имя входа еще не существует, создайте на целевом сервере новое имя входа.  
  
## <a name="TsqlProcedure"></a>Использование Transact-SQL  
  
#### <a name="to-make-a-target-server"></a>Создание целевого сервера  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере текущий сервер прикрепляется к главному серверу AdventureWorks1. Расположение текущего сервера: строение 21, комната 309, стойка 5.  
  
    ```  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_msx_enlist N'AdventureWorks1',   
        N'Building 21, Room 309, Rack 5' ;   
    GO;  
    ```  
  
    Дополнительные сведения см. в разделе [sp_msx_enlist (Transact-SQL)](http://msdn.microsoft.com/en-us/ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f).  
  
## <a name="see-also"></a>См. также:  
[Автоматизация администрирования в масштабах предприятия](../../ssms/agent/automated-administration-across-an-enterprise.md)  
  
