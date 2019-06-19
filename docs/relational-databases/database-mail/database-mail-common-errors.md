---
title: Распространенные ошибки при работе с компонентом Database Mail | Документация Майкрософт
ms.custom: ''
ms.date: 04/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- architecture [SQL Server], Database Mail
- Database Mail [SQL Server], architecture
- Database Mail [SQL Server], components
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d48eeb1d8b18b0cf6cd35b5f6e975ddc426fbf5c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66506952"
---
# <a name="common-errors-with-database-mail"></a>Распространенные ошибки при работе с компонентом Database Mail 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описаны некоторые распространенные ошибки в работе компонента Database Mail и их решения.

## <a name="could-not-find-stored-procedure-spsenddbmail"></a>Хранимая процедура sp_send_dbmail не найдена
Хранимая процедура [sp_send_dbmail](../system-stored-procedures/sp-send-dbmail-transact-sql.md) устанавливается в базе данных msdb. Необходимо выполнять процедуру **sp_send_dbmail** непосредственно из базы данных msdb или указывать трехчастное имя для этой хранимой процедуры.

Пример
```sql
EXEC msdb.dbo.sp_send_dbmail ...
```

или:

```sql
USE msdb;
GO
EXEC dbo.sp_send_dbmail ...
```

Для включения и настройки компонента Database Mail используется [Мастер настройки компонента Database Mail](configure-database-mail.md).

## <a name="profile-not-valid"></a>Недопустимый профиль
Есть две возможные причины возникновения этого сообщения. Указанный профиль не существует или пользователь, выполняющий процедуру [sp_send_dbmail (Transact-SQL)](../system-stored-procedures/sp-send-dbmail-transact-sql.md), не имеет разрешения на доступ к этому профилю.

Чтобы проверить разрешения для профиля, выполните хранимую процедуру [sysmail_help_principalprofile_sp (Transact-SQL)](../system-stored-procedures/sysmail-help-principalprofile-sp-transact-sql.md) с именем профиля. Используйте хранимую процедуру [sysmail_add_principalprofile_sp (Transact-SQL)](../system-stored-procedures/sysmail-help-principalprofile-sp-transact-sql.md) или [мастер настройки компонента Database Mail](configure-database-mail.md), чтобы дать пользователю или группе msdb доступ к профилю.

## <a name="permission-denied-on-spsenddbmail"></a>Отказано в разрешении на sp_send_dbmail

В этом подразделе описывается, как устранить неполадки в случае получения сообщения об ошибке, указывающего на то, что пользователь, который пытается отправить сообщение Database Mail, не имеет разрешения на выполнение процедуры sp_send_dbmail.

Текст ошибки:

```
EXECUTE permission denied on object 'sp_send_dbmail', 
database 'msdb', schema 'dbo'.
```

Чтобы отправить почтовое сообщение Database Mail, необходимо быть пользователем базы данных msdb и членом роли базы данных DatabaseMailUserRole в базе данных msdb. Чтобы добавить пользователей или группы msdb в эту роль, используйте среду SQL Server Management Studio или выполните следующую инструкцию для пользователя или роли, которым требуется отправить сообщение Database Mail.

```sql
EXEC msdb.dbo.sp_addrolemember @rolename = 'DatabaseMailUserRole'
    ,@membername = '<user or role name>';
GO
```
Дополнительные сведения см. в статье [sp_addrolemember](../system-stored-procedures/sp-addrolemember-transact-sql.md) или [sp_droprolemember](../system-stored-procedures/sp-droprolemember-transact-sql.md).

## <a name="database-mail-queued-no-entries-in-sysmaileventlog-or-windows-application-event-log"></a>Письмо поставлено в очередь, но нет записей в представлении sysmail_event_log или в журнале событий Windows 

Для постановки сообщений электронной почты в очередь компонент Database Mail использует компонент Service Broker. Если компонент Database Mail остановлен или функция доставки сообщений компонента Service Broker не активирована в базе данных **msdb**, компонент Database Mail ведет базу данных очереди сообщений, но не имеет возможности отправлять их. В этом случае сообщения компонента Service Broker остаются в очереди Service Broker. Компонент Service Broker не активирует внешнюю программу, поэтому записи в журнале **sysmail_event_log** отсутствуют, а состояние элемента очереди в таблице **sysmail_allitems** и связанных представлениях не обновляется.

Выполните следующую инструкцию в базе данных **msdb**, чтобы проверить, включен ли компонент Service Broker:

```sql
SELECT is_broker_enabled FROM sys.databases WHERE name = 'msdb';
```

Значение 0 указывает на то, что компонент Service Broker не активирован в базе данных msdb для доставки сообщений. Чтобы устранить проблему, активируйте компонент Service Broker в базе данных с помощью следующей команды Transact-SQL:

```sql
USE master ;
GO

ALTER DATABASE msdb SET ENABLE_BROKER ;
GO
``` 

Компонент Database Mail зависит от нескольких внутренних хранимых процедур. Для сокращения контактной зоны эти хранимые процедуры отключены во вновь установленном экземпляре SQL Server. Чтобы включить эти хранимые процедуры, воспользуйтесь параметром [Database Mail XPs](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) системной хранимой процедуры **sp_configure**, как в следующем примере.

```sql
EXEC sp_configure 'show advanced options', 1;  
RECONFIGURE;
EXEC sp_configure 'Database Mail XPs', 1;  
RECONFIGURE  
GO  

Database Mail may be stopped in the **msdb** database. To check status of Database Mail, execute the following statement:

```sql
EXECUTE dbo.sysmail_help_status_sp;
```

Для запуска компонента Database Mail в базе данных обслуживания почты выполните в базе данных msdb следующую команду:

```sql
EXECUTE dbo.sysmail_start_sp;
```

В момент активации компонент Service Broker проверяет продолжительность диалога для сообщений; сообщениям, которые находились в очереди передачи компонента Service Broker дольше, чем установлено настройками продолжительности диалога, немедленно назначается состояние ошибки. Компонент Database Mail обновляет состояние сообщений с ошибками в таблице [sysmail_allitems](../system-catalog-views/sysmail-allitems-transact-sql.md) и связанных представлениях. Вам следует принять решение о целесообразности повторной отправки сообщений. Дополнительные сведения о настройке продолжительности диалога, которая используется компонентом Database Mail, см. в разделе [sysmail_configure_sp (Transact-SQL)](../system-stored-procedures/sysmail-configure-sp-transact-sql.md).



##  <a name="RelatedContent"></a> См. также
  
-  [Общие сведения о компоненте Database Mail](database-mail.md)
-  [Создание профиля компонента Database Mail](create-a-database-mail-profile.md)
  
  
