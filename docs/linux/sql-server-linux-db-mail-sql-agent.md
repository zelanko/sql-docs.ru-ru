---
title: Использование DB Mail и оповещений по электронной почте с агентом SQL в Linux
description: В этой статье описывается использование DB Mail и оповещений по электронной почте с SQL Server на Linux.
author: VanMSFT
ms.author: vanto
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: tbd
ms.openlocfilehash: 31f8931f6e0eddc67b2e58ae794631a9ae6555b7
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68077450"
---
# <a name="db-mail-and-email-alerts-with-sql-agent-on-linux"></a>Использование DB Mail и оповещений по электронной почте с агентом SQL в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ниже приведены основные шаги по настройке компонента DB Mail и его использованию с агентом SQL Server (**mssql-server-agent**) в Linux. 

## <a name="1-enable-db-mail"></a>1. Включите DB Mail

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

## <a name="3-create-a-default-profile"></a>3. Создайте профиль по умолчанию

```sql
EXECUTE msdb.dbo.sysmail_add_profile_sp 
@profile_name = 'default', 
@description = 'Profile for sending Automated DBA Notifications' 
GO
```

## <a name="4-add-the-database-mail-account-to-a-database-mail-profile"></a>4. Добавьте учетную запись Database Mail в профиль компонента Database Mail
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
 
## <a name="6-send-test-email"></a>6. Отправьте тестовое сообщение электронной почты
> [!NOTE]
> Вам может потребоваться перейти в почтовый клиент и разрешить отправку почты менее надежным клиентам. Не все клиенты распознают DB Mail как управляющую программу электронной почты.

```
EXECUTE msdb.dbo.sp_send_dbmail 
@profile_name = 'default', 
@recipients = 'recipient-email@gmail.com', 
@Subject = 'Testing DBMail', 
@Body = 'This message is a test for DBMail' 
GO
```

## <a name="7-set-db-mail-profile-using-mssql-conf-or-environment-variable"></a>7. Настройте профиль DB Mail с помощью mssql-conf или переменной среды
Профиль DB Mail можно зарегистрировать с помощью служебной программы mssql-conf или переменных среды. В данном случае профиль назовем профилем по умолчанию.

```bash
# via mssql-conf
sudo /opt/mssql/bin/mssql-conf set sqlagent.databasemailprofile default
# via environment variable
MSSQL_AGENT_EMAIL_PROFILE=default
```

## <a name="8-set-up-an-operator-for-sqlagent-job-notifications"></a>8. Настройте оператора для уведомлений о заданиях SQLAgent 

```sql
EXEC msdb.dbo.sp_add_operator 
@name=N'JobAdmins',  
@enabled=1, 
@email_address=N'recipient-email@gmail.com',  
@category_name=N'[Uncategorized]' 
GO 
```

## <a name="9-send-email-when-agent-test-job-succeeds"></a>9. Отправьте сообщение электронной почты при успешном выполнении тестового задания агента 

```
EXEC msdb.dbo.sp_update_job 
@job_name='Agent Test Job', 
@notify_level_email=1, 
@notify_email_operator_name=N'JobAdmins' 
GO
```

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения об использовании агента SQL Server для создания, планирования и выполнения заданий см. в статье [Создание и запуск задания агента SQL Server в Linux](sql-server-linux-run-sql-server-agent-job.md).
