---
title: Обеспечение безопасности агента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, security
- security [SQL Server Agent], about security
- security [SQL Server Agent]
- security [SQL Server], SQL Server Agent
ms.assetid: d770d35c-c8de-4e00-9a85-7d03f45a0f0d
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8de2fa7123859a6394459a62570ffc86aab37361
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68262371"
---
# <a name="implement-sql-server-agent-security"></a>Обеспечение безопасности агента SQL Server
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент позволяет администратору базы данных выполнять каждый шаг задания в контексте безопасности, имеющем только те разрешения, которые необходимы для выполнения шага задания, что обеспечивается учетной записью-посредником агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для установки разрешений для конкретного шага задания необходимо создать учетную запись-посредник, обладающую необходимыми разрешениями, а затем назначить ее шагу задания. Учетная запись-посредник может быть назначена нескольким этапам задания. Шагам задания, которым требуются одинаковые разрешения, назначают одну и ту же учетную запись-посредник.  
  
Следующий раздел описывает, какие роли базы данных необходимо предоставить пользователям, чтобы они могли создавать и выполнять задания с помощью агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="granting-access-to-sql-server-agent"></a>Предоставление доступа к агенту SQL Server  
Для доступа к агенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователь должен быть членом одной или нескольких следующих предопределенных ролей базы данных.  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
Эти роли хранятся в базе данных **msdb** . По умолчанию ни один из пользователей ни в одну из этих ролей не входит. Членство в них должно быть предоставлено явным образом. Пользователи, являющиеся членами предопределенной роли сервера **sysadmin** , имеют полный доступ к агенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и им не нужно быть членами перечисленных предопределенных ролей базы данных, чтобы использовать агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если пользователь не является ни членом указанных ролей базы данных, ни членом роли **sysadmin** , узел агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]для него недоступен.  
  
Члены указанных ролей базы данных могут просматривать и выполнять задания, владельцами которых они являются, а также создавать шаги задания, которые выполняются от имени существующих учетных записей-посредников. Дополнительные сведения о конкретных разрешениях, связанных с каждой из этих ролей, см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
Члены предопределенной роли сервера **sysadmin** имеют разрешение на создание, изменение и удаление учетных записей-посредников. Члены роли **sysadmin** имеют разрешение на создание шагов задания без указания учетной записи-посредника, работающих под учетной записью службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , то есть той учетной записи, под которой был запущен агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="guidelines"></a>Рекомендации  
Чтобы повысить защищенность системы безопасности агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следуйте следующим правилам:  
  
-   создавайте специально выделенные учетные записи-посредники, и для выполнения шагов заданий пользуйтесь только ими;  
  
-   предоставляйте разрешения только необходимым учетным записям-посредникам. Предоставляйте только те разрешения, которые действительно необходимы для выполнения шагов задания, которому назначена данная учетная запись-посредник;  
  
-   Не запускайте службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием учетной записи Microsoft Windows, которая является членом группы **Администраторы** Windows.  
  
-   Посредник не может быть безопаснее хранилища учетных данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Если пользовательские операции записи могут создавать события в журнале событий NT, то они могут создавать предупреждения через агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Не следует указывать учетную запись администратора NT в качестве учетной записи службы или учетной записи-посредника.  
  
-   Обратите внимание, что агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеют доступ к ресурсам друг друга. Эти две службы разделяют пространство одного процесса, а агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является пользователем sysadmin для службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Когда TSX регистрируется в MSX, пользователи sysadmin в этих системах MSX получают полный контроль над целевым экземпляром TSX [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   ACE представляет собой расширение, которое ссылаться само на себя. ACE вызывается Chainer ScenarioEngine.exe (также называется Microsoft.SqlServer.Chainer.Setup.exe) или может быть вызван другим процессом на сервере.  
  
-   ACE зависит от следующих библиотек конфигурации DLL, принадлежащих SSDP, поскольку эти API библиотек DLL вызываются ACE:  
  
    -   **SCO** — Microsoft.SqlServer.Configuration.Sco.dll, содержащий новые проверки SCO для виртуальных учетных записей;  
  
    -   **Кластер** — Microsoft.SqlServer.Configuration.Cluster.dll;  
  
    -   **SFC** — Microsoft.SqlServer.Configuration.SqlConfigBase.dll;  
  
    -   **Расширение** — Microsoft.SqlServer.Configuration.ConfigExtension.dll.  
  
## <a name="see-also"></a>См. также:  
[Использование стандартных ролей](../../reporting-services/security/role-definitions-predefined-roles.md)  
[Хранимая процедура Хранимая процедура sp_addrolemember (Transact-SQL)](https://msdn.microsoft.com/a583c087-bdb3-46d2-b9e5-3921b3e6d10b)  
[sp_droprolemember (Transact-SQL)](https://msdn.microsoft.com/c2f19ab1-e742-4d56-ba8e-8ffd40cf4925)  
[Защита и обеспечение безопасности (ядро СУБД)](https://msdn.microsoft.com/dfb39d16-722a-4734-94bb-98e61e014ee7)  
  
