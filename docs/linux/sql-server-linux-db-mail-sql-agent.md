---
title: "DB Mail и оповещения по электронной почте с агентом SQL Server для Linux | Документы Microsoft"
description: "В этом разделе описывается использование компонента DB Mail и оповещения по электронной почте с помощью SQL Server в Linux"
author: meet-bhagdev
ms.author: meetb
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: tbd
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 838a7d492f9826d966da205fc4727eae48ff6e42
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="db-mail-and-email-alerts-with-sql-agent-on-linux"></a>DB Mail и оповещения по электронной почте с агентом SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Следующие шаги показывают, как настройка компонента DB Mail и использовать его с помощью агента SQL Server (**mssql-server-agent**) в Linux. 

> [!NOTE]
> Для использования компонента DB Mail с SQL Server в Linux, необходимо использовать SQL Server 2017 г RC2 или более поздней версии.

## <a name="prerequisites"></a>Предварительные требования
-   SQL Server 2017 г., RC2 и более поздних версий
-   Агент SQL Server v14.0.800.90-2 и выше (Если вы планируете использовать электронной почты для оповещений)

## <a name="1-enable-db-mail"></a>1. Включение компонента DB Mail

```sql
USE master 
GO 
sp_configure 'show advanced options',1 
GO 
RECONFIGURE WITH OVERRIDE 
GO 
sp_configure 'Database Mail XPs', 1 
GO 
RECONFIGURE  
GO  
```

## <a name="2-create-a-new-account"></a>2. Создать новую учетную запись
```sql
EXECUTE msdb.dbo.sysmail_add_account_sp 
@account_name = 'SQLAlerts', 
@description = 'Account for Automated DBA Notifications', 
@email_address = 'sqlagenttest@gmail.com', 
@replyto_address = 'sqlagenttest@gmail.com', 
@display_name = 'SQL Agent', 
@mailserver_name = 'smtp.gmail.com', 
@port = 587, 
@enable_ssl = 1, 
@username = 'sqlagenttest@gmail.com', 
@password = '<password>' 
GO
```

## <a name="3-create-a-default-profile"></a>3. Создание профиля по умолчанию

```sql
EXECUTE msdb.dbo.sysmail_add_profile_sp 
@profile_name = 'default', 
@description = 'Profile for sending Automated DBA Notifications' 
GO
```

## <a name="4-add-the-database-mail-account-to-a-database-mail-profile"></a>4. Добавьте учетную запись компонента Database Mail для профиля компонента Database Mail
```sql
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp 
@profile_name = 'default', 
@principal_name = 'public', 
@is_default = 1 ; 
 ```
 
## <a name="5-add-account-to-profile"></a>5. Добавьте учетную запись в профиль 
```sql
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp   
@profile_name = 'default',   
@account_name = 'SQLAlerts',   
@sequence_number = 1;  
 ```
 
## <a name="6-send-test-email"></a>6. Отправить тестовое сообщение электронной почты
> [!NOTE]
> Возможно перейти к клиент электронной почты и установите флажок «Разрешать опаснее клиентами для отправки почты.» Не все клиенты считают компонента DB Mail управляющая программа электронной почты.

```
EXECUTE msdb.dbo.sp_send_dbmail 
@profile_name = 'default', 
@recipients = 'recipient-email@gmail.com', 
@Subject = 'Testing DBMail', 
@Body = 'This message is a test for DBMail' 
GO
```

## <a name="7-set-db-mail-profile-using-mssql-conf-or-environment-variable"></a>7. Установить профиль электронной почты базы данных с помощью mssql conf или переменную среды
Для регистрации профиль компонента DB Mail предназначена программа mssql conf или переменных среды. В этом случае назовем профиль по умолчанию.

```bash
# via mssql-conf
sudo /opt/mssq/bin/mssql-conf set sqlagent.databasemailprofile default
# via environment variable
MSSQL_AGENT_EMAIL_PROFILE=default
```

## <a name="8-set-up-an-operator-for-sqlagent-job-notifications"></a>8. Настройка оператора для уведомления о задании SQLAgent 

```sql
EXEC msdb.dbo.sp_add_operator 
@name=N'JobAdmins',  
@enabled=1, 
@email_address=N'recipient-email@gmail.com',  
@category_name=N'[Uncategorized]' 
GO 
```

## <a name="9-send-email-when-agent-test-job-succeeds"></a>9. Отправить по электронной почте после успешного завершения «Задание агента тестирования» 

```
EXEC msdb.dbo.sp_update_job 
@job_name='Agent Test Job', 
@notify_level_email=1, 
@notify_email_operator_name=N'JobAdmins' 
GO
```

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения о том, как использовать для создания, планирования и запуска заданий агента SQL Server см. в разделе [запуска задания агента SQL Server в Linux](sql-server-linux-run-sql-server-agent-job.md).

