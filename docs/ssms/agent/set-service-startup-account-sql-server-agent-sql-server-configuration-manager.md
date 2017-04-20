---
title: "Назначение учетной записи для запуска службы агента SQL Server | Документация Майкрософт"
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
- SQL Server Agent, service accounts
- startup accounts [SQL Server]
- service startup accounts [SQL Server Agent]
ms.assetid: 46ffe818-ebb5-43a0-840b-923f219a2472
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ca20cf42839419f5d40826ef992087623dbc3059
ms.lasthandoff: 04/11/2017

---
# <a name="set-the-service-startup-account-for-sql-server-agent-sql-server-configuration-manager"></a>Назначение стартовой учетной записи службы для агента SQL Server (диспетчер конфигурации SQL Server)
Стартовая учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] определяет учетную запись Windows, которая запускает агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , а также его сетевые разрешения. Этот раздел посвящен назначению учетных записей службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
**В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   [Назначение стартовой учетной записи службы для службы агента SQL Server при помощи среды SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)], агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] больше не требует, чтобы стартовая учетная запись была элементом группы администраторов [!INCLUDE[msCoName](../../includes/msconame_md.md)] . Однако стартовая учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] должна быть членом предопределенной роли сервера sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Чтобы использовать обработку заданий в многосерверной среде, учетная запись должна быть членом роли "TargetServersRole" базы данных "msdb" на главном сервере.  
  
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
  
#### <a name="to-set-the-service-startup-account-for-sql-server-agent"></a>Назначение стартовой учетной записи службы агента SQL Server  
  
1.  В списке **Зарегистрированные серверы**щелкните знак «плюс», чтобы развернуть **Ядро СУБД**.  
  
2.  Чтобы развернуть папку **Группы локальных серверов** , щелкните знак «плюс» (+).  
  
3.  Щелкните правой кнопкой мыши экземпляр сервера, в котором нужно назначить стартовую учетную запись службы, и выберите **Диспетчер конфигурации SQL Server...**  
  
4.  В диалоговом окне **Контроль учетных записей** нажмите кнопку **Да**.  
  
5.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] на панели консоли выберите **Службы SQL Server**.  
  
6.  В области сведений щелкните правой кнопкой **Агент SQL Server***имя_сервера*, где *имя_сервера* — это имя экземпляра агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], для которого необходимо изменить стартовую учетную запись службы, и выберите пункт **Свойства**.  
  
7.  В диалоговом окне **Свойства агента SQL Server***(имя_сервера)***** выберите на вкладке **Вход в систему** один из следующих параметров в разделе **Использовать для входа**:  
  
    -   **Встроенная учетная запись**. Выберите этот параметр, если заданиям требуются ресурсы только с локального сервера. Дополнительные сведения о выборе типа встроенной учетной записи Windows см. в разделе [Выбор учетной записи для службы агента SQL Server.](http://msdn.microsoft.com/library/ms191543.aspx)  
  
        > [!IMPORTANT]  
        > Служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] не поддерживает учетную запись **Локальная служба** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
    -   **Указанная учетная запись**. Выберите этот параметр, если заданиям требуются сетевые ресурсы (в том числе ресурсы приложений), а также если необходимо передавать события журналам других программ Windows или уведомлять операторов по электронной почте или на пейджер.  
  
        В случае использования этого параметра:  
  
        1.  В поле **Имя учетной записи** введите учетную запись, которая будет использоваться для запуска агента SQL Server. Или нажмите кнопку **Обзор** , чтобы открыть диалоговое окно **Выбор пользователя или группы** , и выберите учетную запись для использования.  
  
        2.  В поле **Пароль** введите пароль, соответствующий учетной записи. Повторно введите пароль в поле **Подтверждение пароля** .  
  
8.  Нажмите кнопку **ОК**.  
  
9. В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] нажмите кнопку **Закрыть** .  
  

