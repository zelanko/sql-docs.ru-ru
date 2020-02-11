---
title: Настройка стартовой учетной записи службы для агент SQL Server (диспетчер конфигурации SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- startup accounts [SQL Server]
- service startup accounts [SQL Server Agent]
ms.assetid: 46ffe818-ebb5-43a0-840b-923f219a2472
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 30c50d1f6efc44c17eac76e0e03432c2461da296
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63033690"
---
# <a name="set-the-service-startup-account-for-sql-server-agent-sql-server-configuration-manager"></a>Set the Service Startup Account for SQL Server Agent (SQL Server Configuration Manager)
  Стартовая учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет учетную запись Windows, которая запускает агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а также его сетевые разрешения. Этот раздел посвящен назначению учетных записей службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   [Настройка стартовой учетной записи службы для агент SQL Server с помощью SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] больше не требует, чтобы стартовая учетная запись была элементом группы администраторов [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Однако стартовая учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должна быть членом предопределенной роли сервера sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы использовать обработку заданий в многосерверной среде, учетная запись должна быть членом роли "TargetServersRole" базы данных "msdb" на главном сервере.  
  
-   Узел агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отображается в обозревателе объектов только при наличии у пользователя разрешения на использование узла.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для выполнения своих функций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент должен быть настроен на использование учетных данных учетной записи, которая является членом `sysadmin` предопределенной роли сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в. Эта учетная запись должна иметь следующие разрешения Windows.  
  
-   Вход в систему в качестве службы (SeServiceLogonRight)  
  
-   Замена токена уровня процесса (SeAssignPrimaryTokenPrivilege)  
  
-   Обход проходной проверки (SeChangeNotifyPrivilege)  
  
-   Назначение квот памяти процессам (SeIncreaseQuotaPrivilege)  
  
 Дополнительные сведения о разрешениях Windows, необходимых для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи службы агента, см. в разделе [Выбор учетной записи для службы агент SQL Server](select-an-account-for-the-sql-server-agent-service.md) и [Настройка учетных записей службы Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-set-the-service-startup-account-for-sql-server-agent"></a>Назначение стартовой учетной записи службы агента SQL Server  
  
1.  В списке **Зарегистрированные серверы**щелкните знак «плюс», чтобы развернуть **Ядро СУБД**.  
  
2.  Чтобы развернуть папку **Группы локальных серверов** , щелкните знак «плюс» (+).  
  
3.  Щелкните правой кнопкой мыши экземпляр сервера, в котором нужно назначить стартовую учетную запись службы, и выберите **Диспетчер конфигурации SQL Server...**  
  
4.  В диалоговом окне **Контроль учетных записей** нажмите кнопку **Да**.  
  
5.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на панели консоли выберите **Службы SQL Server**.  
  
6.  В области сведений щелкните правой кнопкой мыши **Агент SQL Server**_(server_name)_, где *server_name* — имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента, для которого необходимо изменить стартовую учетную запись службы, и выберите пункт **Свойства**.  
  
7.  В диалоговом окне **свойства** **Агент SQL Server**_(server_name)_ на вкладке **Вход** в систему выберите один из следующих параметров в разделе **Вход в систему как**.  
  
    -   **Встроенная учетная запись**. Выберите этот параметр, если заданиям требуются ресурсы только с локального сервера. Дополнительные сведения о выборе типа встроенной учетной записи Windows см. в разделе [Выбор учетной записи для службы агента SQL Server.](https://msdn.microsoft.com/library/ms191543.aspx)  
  
        > [!IMPORTANT]  
        >  Служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает учетную запись **Локальная служба** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
    -   **Эта учетная запись**: Выберите этот параметр, если заданиям требуются ресурсы по сети, включая ресурсы приложения. Если требуется перенаправить события в другие журналы приложений Windows; или, если вы хотите уведомлять операторов по электронной почте или на пейджерах.  
  
         В случае использования этого параметра:  
  
        1.  В поле **Имя учетной записи** введите учетную запись, которая будет использоваться для запуска агента SQL Server. Или нажмите кнопку **Обзор** , чтобы открыть диалоговое окно **Выбор пользователя или группы** , и выберите учетную запись для использования.  
  
        2.  В поле **Пароль** введите пароль, соответствующий учетной записи. Повторно введите пароль в поле **Подтверждение пароля** .  
  
8.  Нажмите кнопку **ОК**.  
  
9. В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нажмите кнопку **Закрыть** .  
  
  
