---
title: Устранение общих неполадок компонента Database Mail с помощью SQL Server | Документация Майкрософт
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
ms.openlocfilehash: 304306edc78229899b0660b99df6f6b78b60e6ca
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72906074"
---
# <a name="general-database-mail-troubleshooting-steps"></a>Общие действия по устранению неполадок компонента Database Mail 
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

Устранение неполадок с компонентом Database Mail включает проверку следующих основных областей системы Database Mail. Эти процедуры перечислены в логическом порядке, однако порядок выполнения может быть любым другим.

## <a name="permissions"></a>Разрешения

Для устранения неполадок любого рода с компонентом Database Mail необходимо быть членом предопределенной роли сервера sysadmin. Пользователи, не являющиеся членами предопределенной роли сервера sysadmin, могут только получать сведения о сообщениях, которые они пытались отправить. Сведения о сообщениях других пользователей им недоступны.

## <a name="is-database-mail-enabled"></a>Включен ли компонент Database Mail

1. В среде SQL Server Management Studio подключитесь к экземпляру SQL Server в окне редактора запросов, после чего выполните следующий код:

    ```sql
    sp_configure 'show advanced', 1; 
    GO
    RECONFIGURE;
    GO
    sp_configure;
    GO
    ```

   В области результатов убедитесь, что run_value для [Database Mail XPs](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) имеет значение 1.
   Если run_value не равно 1, компонент Database Mail не включен. Компонент Database Mail не включается автоматически, что сделано для уменьшения числа функций, доступных для атаки злонамеренным пользователем. Дополнительные сведения см. в разделе [Основные сведения о настройке контактной зоны в библиотеке MSDN](../security/surface-area-configuration.md).

1. Если принято решение о необходимости включения компонента Database Mail, выполните следующий код:

    ```sql
    sp_configure 'Database Mail XPs', 1; 
    GO
    RECONFIGURE;
    GO
    ```

1. Чтобы восстановить процедуру sp_configure в состояние по умолчанию, в котором не отображаются дополнительные параметры, выполните следующий код:

    ```sql 
    sp_configure 'show advanced', 0; 
    GO
    RECONFIGURE;
    GO
    ```

## <a name="are-users-properly-configured-to-send-mail"></a>Правильно ли у пользователей настроена отправка почты

1. Чтобы отправлять почту через компонент Database Mail, пользователю необходимо быть членом роли DatabaseMailUserRole в базе данных msdb. Члены предопределенной роли сервера sysadmin и роли msdb db_owner автоматически являются членами роли DatabaseMailUserRole. Для получения списка всех членов роли DatabaseMailUserRole выполните следующую инструкцию:

    ```sql
    EXEC msdb.sys.sp_helprolemember 'DatabaseMailUserRole';
    ```

1. Для предоставления пользователю роли DatabaseMailUserRole выполните следующую инструкцию:

    ```sql
    USE msdb;
    GO
    
    sp_addrolemember @rolename = 'DatabaseMailUserRole'
    ,@membername = '<database user>';
    ```

1. Для отправки сообщений через компонент Database Mail пользователям необходим доступ как минимум к одному из его профилей. Для получения списка пользователей (участников) и профилей, к которым у них есть доступ, выполните следующую инструкцию:

    ```sql
    EXEC msdb.dbo.sysmail_help_principalprofile_sp;
    ```

1. Воспользуйтесь мастером настройки компонента Database Mail, чтобы создавать профили и предоставлять пользователям доступ к ним.
 
## <a name="is-database-mail-started"></a>Запущен ли компонент Database Mail

1. [Внешняя программа компонента Database Mail](database-mail-external-program.md) активируется, когда нужно выполнить обработку электронных сообщений. Если в течение указанного времени ожидания сообщений для отправки нет, программа завершает работу. Для подтверждения активации компонента Database Mail выполните следующую инструкцию:

    ```sql
    EXEC msdb.dbo.sysmail_help_status_sp;
    ```
1. Если активация компонента Database Mail не началась, выполните следующую инструкцию, чтобы запустить его:

    ```sql
    EXEC msdb.dbo.sysmail_start_sp;
    ```

1. Если запущена внешняя программа компонента Database Mail, проверьте состояние очереди почты с помощью следующей инструкции:

    ```sql
    EXEC msdb.dbo.sysmail_help_queue_sp @queue_type = 'mail';
    ```
  
   Почтовая очередь должна находиться в состоянии RECEIVES_OCCURRING. В различные моменты времени состояние очереди может изменяться. Если состояние очереди почты отличается от RECEIVES_OCCURRING, попробуйте перезагрузить очередь. Остановите очередь при помощи следующей инструкции.
   
```sql
EXEC msdb.dbo.sysmail_stop_sp;
```

Запустите очередь при помощи следующей инструкции.

```sql
EXEC msdb.dbo.sysmail_start_sp;
```

  > [!NOTE]
  >  Столбец length в результирующем наборе процедуры sysmail_help_queue_sp позволяет определить количество сообщений электронной почты, находящихся в очереди.

## <a name="do-problems-affect-some-or-all-accounts"></a>Проблемы оказывают влияние лишь на некоторые или на все учетные записи

1. Если выяснилось, что отправлять почту могут только некоторые профили, проблема, вероятно, относится к учетным записям компонента Database Mail, которые пользуются неисправными профилями. Чтобы определить, какие из учетных записей успешно отправляют почтовые сообщения, выполните следующую инструкцию:

    ```sql
    SELECT sent_account_id, sent_date FROM msdb.dbo.sysmail_sentitems;
    ```

1. Если неработающий профиль не используется ни одной из перечисленных учетных записей, может оказаться, что ни одна учетная запись, доступная в профиле, не работает правильно. Для проверки отдельных учетных записей воспользуйтесь мастером настройки компонента Database Mail для создания нового профиля с единственной учетной записью и затем используйте диалоговое окно "Отправка тестового сообщения", чтобы отправить почту через новую учетную запись. 
1. Для просмотра сообщений об ошибках, возвращаемых компонентом Database Mail, выполните следующую инструкцию:

    ```sql
    SELECT * FROM msdb.dbo.sysmail_event_log;
    ```

   > [!NOTE]
   > Компонент Database Mail считает почтовое сообщение отправленным, когда оно успешно доставлено на почтовый SMTP-сервер. Успешной доставке сообщения могут помешать и другие ошибки, возникшие при дальнейшей обработке (например, неверный адрес получателя), но они уже не отражаются в журнале компонента Database Mail.

## <a name="retry-mail-delivery"></a>Повторите попытку доставки сообщения

1. Если обнаружилось, что в работе компонента Database Mail происходят сбои из-за недоступности SMTP-сервера, можно повысить число успешных доставок путем увеличения числа попыток, предпринимаемых компонентом Database Mail при отправке каждого сообщения. Запустите мастер настройки компонента Database Mail и выберите "Просмотр или изменение системных параметров". Можно также связать с профилем несколько учетных записей; в этом случае, при наличии главной учетной записи отработки отказа, компонент Database Mail будет использовать ее для отправки сообщений.
1. На странице настроек системных параметров значения по умолчанию 60 для параметра "Количество попыток применения учетной записи" и 5 секунд для параметра "Интервал между попытками применения учетной записи" означают, что доставка сообщения не удалась, если SMTP-сервер был недоступен в течение 5 минут. Увеличьте значения этих параметров, чтобы продлить время ожидания во время отправки сообщения.

    > [!NOTE]
    > При массовой отправке сообщений большие значения по умолчанию могут повысить надежность, но при этом они существенно повышают потребление ресурсов, так как приводят к многократным попыткам отправки большого количества сообщений. Лучше выявите и устраните первопричину этого явления, которая может оказаться проблемой сети или SMTP-сервера, мешающей компоненту Database Mail нормально соединяться с SMTP-сервером.



##  <a name="RelatedContent"></a> См. также
  
-   [Объекты конфигурации компонента Database Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)  
  
-   [Объекты обмена сообщениями компонента Database Mail](../../relational-databases/database-mail/database-mail-messaging-objects.md)  
  
-   [Внешняя программа компонента Database Mail](../../relational-databases/database-mail/database-mail-external-program.md)  
  
-   [Ведение журнала и аудит компонента Database Mail](../../relational-databases/database-mail/database-mail-log-and-audits.md)  
  
-   [Настройка почты агента SQL Server на использование компонента Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
  
  
