---
title: "Настройка псевдонима SQL Server для службы агента SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aliases [SQL Server], creating
- SQL Server Agent, aliases
ms.assetid: 02d6295d-ab52-44f0-8f1b-f3910a507d8f
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8ab5a19e73661e5695bd98f3469c507f328c12a3
ms.lasthandoff: 04/11/2017

---
# <a name="set-a-sql-server-alias-for-the-sql-server-agent-service-sql-server-management-studio"></a>Set a SQL Server Alias for the SQL Server Agent Service (SQL Server Management Studio)
В этом разделе описано, как задать псевдоним [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] для использования при соединении с компонентом [!INCLUDE[ssDE](../../includes/ssde_md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. По умолчанию служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] соединяется с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] через именованные каналы по динамическим именам серверов, которые не требуют дополнительной настройки клиента. Необходимо настроить только псевдоним соединения сервера, если не используется установленный по умолчанию сетевой механизм передачи данных или если происходит подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , прослушивающему по альтернативному именованному каналу.  
  
**В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   [Настройка псевдонима SQL Server для службы агента SQL Server в среде SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] не будет работать правильно до тех пор, пока не будет выбран псевдоним, относящийся к местному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Узел агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] отображается в обозревателе объектов только при наличии у пользователя разрешения на использование узла.  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Для выполнения своих функций агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] должен быть настроен на использование учетных данных записи, которая является членом предопределенной роли сервера **sysadmin** в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Эта учетная запись должна иметь следующие разрешения Windows.  
  
-   Вход в систему в качестве службы (SeServiceLogonRight)  
  
-   Замена токена уровня процесса (SeAssignPrimaryTokenPrivilege)  
  
-   Обход проходной проверки (SeChangeNotifyPrivilege)  
  
-   Назначение квот памяти процессам (SeIncreaseQuotaPrivilege)  
  
Дополнительные сведения о разрешениях Windows, необходимых для учетной записи службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , см. в разделах [Выбор учетной записи для службы агента SQL Server](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) и [Настройка учетных записей служб Windows](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014).  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-set-a-sql-server-alias-for-the-sql-server-agent-service"></a>Настройка псевдонима SQL Server для службы агента SQL Server  
  
1.  В **Обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)] и раскройте его.  
  
2.  Щелкните правой кнопкой мыши **агент SQL Server**, затем выберите **Свойства**.  
  
3.  В диалоговом окне **Свойства агента SQL***имя_сервера* в разделе **Выберите страницу**выберите **Соединение**и  
  
4.  в поле **Псевдоним локального хоста сервера** введите псевдоним сервера, с которым должен соединяться агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
5.  Нажмите кнопку **ОК**.  
  

