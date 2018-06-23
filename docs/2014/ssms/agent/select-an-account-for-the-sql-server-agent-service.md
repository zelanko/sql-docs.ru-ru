---
title: Выбор учетной записи для службы агента SQL Server | Документация Майкрософт
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
- roles [SQL Server], SQL Server Agent
- SQL Server Agent, accounts
- startup accounts [SQL Server]
- SQL Server Agent service, accounts
- accounts [SQL Server], SQL Server Agent
- Windows groups [SQL Server Agent]
- SQL Server Agent, permissions
- members [SQL Server], SQL Server Agent service
- Windows domain accounts [SQL Server]
- security [SQL Server], SQL Server Agent
ms.assetid: fe658e32-9e6b-4147-a189-7adc3bd28fe7
caps.latest.revision: 44
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ab05d53c3c9f989252ab248305f000033ff54ccf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195296"
---
# <a name="select-an-account-for-the-sql-server-agent-service"></a>Выбор учетной записи для службы агента SQL Server
  Стартовая учетная запись службы определяет учетную запись [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, с которой запускается агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а также его сетевые разрешения. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется как заданная учетная запись пользователя. Диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет выбрать учетную запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из следующих вариантов:  
  
-   **Встроенная учетная запись**. Может быть выбрана из списка следующих встроенных учетных записей Windows:  
  
    -   Учетная запись**Локальная система** . Имя этой учетной записи — NT AUTHORITY\System. Эта учетная запись имеет неограниченный доступ ко всем локальным системным ресурсам. Она входит в группу **Администраторы** локального компьютера и поэтому является членом предопределенной роли сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sysadmin** .  
  
        > [!IMPORTANT]  
        >  Параметр **С системной учетной записью** поддерживается для обратной совместимости. Локальная системная учетная запись обладает разрешениями, которые не нужны для работы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Старайтесь не запускать агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] от имени учетной записи локальной системы. В целях безопасности рекомендуется пользоваться учетной записью домена Windows с разрешениями, перечисленными в подразделе «Разрешения учетной записи домена Windows» ниже в этом разделе.  
  
-   **Указанная учетная запись**. Позволяет задать учетную запись домена Windows, с которой выполняется служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Рекомендуется выбирать учетную запись пользователя Windows, не входящего в группу **Администраторы** . Однако существуют ограничения при администрировании нескольких серверов, когда учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не входит в локальную группу **Администраторы** . Дополнительные сведения см. в подразделе «Поддерживаемые типы учетных записей» далее в этом разделе.  
  
## <a name="windows-domain-account-permissions"></a>Разрешения учетной записи домена Windows  
 В целях повышения безопасности выбирайте пункт **Указанная учетная запись**, соответствующий учетной записи домена Windows. Заданная учетная запись домена Windows должна обладать следующими разрешениями:  
  
-   Разрешение на вход в систему в качестве службы во всех версиях Windows (SeServiceLogonRight)  
  
> [!NOTE]  
>  Служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должна быть членом группы «Доступ, совместимый с версиями Windows до 2000» контроллера домена. В противном случае задания, принадлежащие пользователям домена, которые не являются администраторами Windows, выполняться не будут.  
  
-   На серверах Windows учетной записи, с которой выполняется служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для поддержки посредников агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимы следующие разрешения:  
  
    -   Разрешение на обход перекрестной проверки (SeChangeNotifyPrivilege)  
  
    -   Разрешение на замену токена уровня процесса (SeAssignPrimaryTokenPrivilege)  
  
    -   Разрешение на выделение процессам квот памяти (SeIncreaseQuotaPrivilege)  
  
    -   Разрешение на вход в систему с помощью входа пакетного типа (SeBatchLogonRight)  
  
> [!NOTE]  
>  Если учетная запись не обладает разрешениями на поддержку посредников, то создавать задания могут только члены предопределенной роли сервера **sysadmin** .  
  
> [!NOTE]  
>  Чтобы получать уведомление о предупреждении инструментария WMI, учетной записи службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должно быть предоставлено разрешение на пространство имен, содержащее события WMI и ALTER ANY EVENT NOTIFICATION.  
  
## <a name="sql-server-role-membership"></a>Членство в ролях SQL Server  
 Учетная запись, от которой запускается служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должна быть членом следующих ролей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   Учетная запись должна быть членом предопределенной роли сервера **sysadmin** .  
  
-   Чтобы использовать обработку заданий в многосерверной среде, учетная запись должна быть членом роли базы данных **msdb** **TargetServersRole** на главном сервере.  
  
## <a name="supported-service-account-types"></a>Поддерживаемые типы учетных записей  
 В следующей таблице перечислены типы учетных записей Windows, которые могут быть использованы для службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Тип учетной записи|Некластеризованный сервер|Кластеризованный сервер|Контроллер домена (некластеризованный)|  
|--------------------------|---------------------------|----------------------|------------------------------------------|  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Учетная запись Windows (член группы "Администраторы" Windows)|Поддерживается|Поддерживается|Поддерживается|  
|Неадминистративная учетная запись домена Windows|Поддерживается<sup>1</sup>|Поддерживается<sup>1</sup>|Поддерживается<sup>1</sup>|  
|Учетная запись сетевой службы (NT AUTHORITY\NetworkService)|Поддерживается<sup>1, 3, 4</sup>|Не поддерживается|Не поддерживается|  
|Неадминистративная учетная запись локального пользователя|Поддерживается<sup>1</sup>|Не поддерживается|Неприменимо|  
|Учетная запись Local System (NT AUTHORITY\System)|Поддерживается<sup>2</sup>|Не поддерживается|Поддерживается<sup>2</sup>|  
|Учетная запись локальной службы (NT AUTHORITY\NetworkService)|Не поддерживается|Не поддерживается|Не поддерживается|  
  
 <sup>1</sup> см.  
  
 <sup>2</sup> ограничение 2 ниже в разделе.  
  
 <sup>3</sup> ограничение 3 ниже в разделе.  
  
 <sup>4</sup> ограничение 4 ниже в разделе.  
  
### <a name="limitation-1-using-non-administrative-accounts-for-multiserver-administration"></a>Ограничение 1. Использование неадминистративных учетных записей для администрирования нескольких серверов  
 Прикрепление целевого сервера к главному серверу может завершиться ошибкой, после чего появляется следующее сообщение: "Не удалось выполнить операцию прикрепления".  
  
 Чтобы устранить эту ошибку, перезапустите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в статье [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).  
  
### <a name="limitation-2-using-the-local-system-account-for-multiserver-administration"></a>Ограничение 2. Использование учетной записи Local System для администрирования нескольких серверов  
 Администрирование нескольких серверов поддерживается при выполнении службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под учетной записью Local System только в том случае, если целевой и главный серверы расположены на одном и том же компьютере. При использовании этой конфигурации, при прикреплении целевого сервера к главному серверу, возвращается следующее сообщение:  
  
 "Убедитесь, что стартовая учетная запись агента для *<имя_компьютера_целевого_сервера>* имеет права для входа на сервер targetServer".  
  
 Данное сообщение можно пропустить. Операция прикрепления должна быть завершена успешно. Дополнительные сведения см. в статье [Создание многосерверной среды](create-a-multiserver-environment.md).  
  
### <a name="limitation-3-using-the-network-service-account-when-it-is-a-sql-server-user"></a>Ограничение 3. Использование учетной записи сетевой службы, которая является учетной записью SQL Server  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] При запуске агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может произойти сбой, если он запускается под учетной записью сетевой службы, которая уже явным образом получила доступ к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Для решения этой проблемы перезагрузите компьютер, на котором работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Это действие необходимо выполнить однократно.  
  
### <a name="limitation-4-using-the-network-service-account-when-sql-server-reporting-services-is-running-on-the-same-computer"></a>Ограничение 4. Использование учетной записи сетевой службы при выполнении служб SQL Server Reporting Services на том же самом компьютере  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент не может быть запущен, если служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется под учетной записью сетевой службы, а службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] запущены на этом же самом компьютере.  
  
 Для решения этой проблемы перезагрузите компьютер, на котором работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а затем перезапустите службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Это действие необходимо выполнить однократно.  
  
## <a name="common-tasks"></a>Общие задачи  
 **Указание стартовой учетной записи службы агента SQL Server**  
  
-   [Назначение стартовой учетной записи службы для агента SQL Server &#40;диспетчер конфигурации SQL Server&#41;](set-service-startup-account-sql-server-agent-sql-server-configuration-manager.md)  
  
 **Указание профиля электронной почты агента SQL Server**  
  
-   [Настройка почты агента SQL Server на использование компонента Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
> [!NOTE]  
>  Запуск агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] во время старта операционной системы задается с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Настройка учетных записей службы Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)   
 [Инструкции по управлению службами (диспетчер конфигурации SQL Server)](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md)   
 [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md)  
  
  