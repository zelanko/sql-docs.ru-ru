---
title: Настройка псевдонима SQL Server для службы агента SQL Server (SQL Server Management Studio) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- aliases [SQL Server], creating
- SQL Server Agent, aliases
ms.assetid: 02d6295d-ab52-44f0-8f1b-f3910a507d8f
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8fc41f1f9916f13a2edc5c2327e9d9ad65bef210
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195004"
---
# <a name="set-a-sql-server-alias-for-the-sql-server-agent-service-sql-server-management-studio"></a>Set a SQL Server Alias for the SQL Server Agent Service (SQL Server Management Studio)
  В этом разделе описано, как задать псевдоним [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для использования при соединении с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)] в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. По умолчанию служба агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] соединяется с экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] через именованные каналы по динамическим именам серверов, которые не требуют дополнительной настройки клиента. Необходимо настроить только псевдоним соединения сервера, если не используется установленный по умолчанию сетевой механизм передачи данных или если происходит подключение к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , прослушивающему по альтернативному именованному каналу.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   [Настройка псевдонима SQL Server для службы агента SQL Server в среде SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] не будет работать правильно до тех пор, пока не будет выбран псевдоним, относящийся к местному экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Узел агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] отображается в обозревателе объектов только при наличии у пользователя разрешения на использование узла.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для выполнения своих функций агент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] должен быть настроен на использование учетных данных записи, которая является членом предопределенной роли сервера **sysadmin** в среде [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Эта учетная запись должна иметь следующие разрешения Windows.  
  
-   Вход в систему в качестве службы (SeServiceLogonRight)  
  
-   Замена токена уровня процесса (SeAssignPrimaryTokenPrivilege)  
  
-   Обход проходной проверки (SeChangeNotifyPrivilege)  
  
-   Назначение квот памяти процессам (SeIncreaseQuotaPrivilege)  
  
 Дополнительные сведения о разрешениях Windows, необходимых для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] учетная запись службы агента. в разделе [выберите учетную запись для службы агента SQL Server](../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) и [Настройка учетных записей службы Windows и Разрешения](configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-set-a-sql-server-alias-for-the-sql-server-agent-service"></a>Настройка псевдонима SQL Server для службы агента SQL Server  
  
1.  В **Обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] и раскройте его.  
  
2.  Щелкните правой кнопкой мыши **агент SQL Server**, затем выберите **Свойства**.  
  
3.  В диалоговом окне **Свойства агента SQL***имя_сервера* в разделе **Выберите страницу** выберите **Соединение** и  
  
4.  в поле **Псевдоним локального хоста сервера** введите псевдоним сервера, с которым должен соединяться агент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
5.  Нажмите кнопку **ОК**.  
  
  