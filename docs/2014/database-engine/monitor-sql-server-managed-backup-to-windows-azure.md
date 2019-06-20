---
title: Монитор SQL Server управляемое резервное копирование в Windows Azure | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: cfb9e431-7d4c-457c-b090-6f2528b2f315
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b7b7b6cc8127b339a45a5f651af6db4d0b595b80
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62844679"
---
# <a name="monitor-sql-server-managed-backup-to-windows-azure"></a>Отслеживание управляемого резервного копирования SQL Server в Windows Azure
  В [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] предусмотрены встроенные меры по определению неполадок и ошибок в процессе резервного копирования, а также действия по исправлению, когда это возможно.  Однако есть некоторые решения, для которых требуется участие пользователя. В этом разделе описаны средства, с помощью которых можно определять общее состояние исправности резервных копий, а также определять любые ошибки, которые требуют устранения.  
  
## <a name="overview-of-includesssmartbackupincludesss-smartbackup-mdmd-built-in-debugging"></a>Обзор встроенной отладки [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] периодически просматривает запланированные сеансы резервного копирования и пытается повторно запланировать те, что завершились с ошибками. Он периодически опрашивает учетную запись хранения, чтобы найти разрыв в цепочке журналов, влияющий на восстанавливаемость базы данных, и планирует соответствующим образом новое резервное копирование. Кроме того, агент учитывает политику регулирования Windows Azure, и в нем предусмотрены механизмы для управления несколькими резервными копиями баз данных. Служба [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] использует расширенные события для отслеживания всех действий. Далее перечислены каналы расширенных событий, используемые агентом [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]: Admin, Operational, Analytical и Debug. События, относящиеся к категории Admin, обычно связаны с ошибками, требуют вмешательства пользователя и включены по умолчанию. События Analytical также включены по умолчанию, но обычно не связаны с ошибками, требующими вмешательства пользователя. События операций обычно информационные. Например к событиям операций относится Планирование резервного копирования, успешное завершение резервного копирования, и т.д. Debug — наиболее детальным и используется внутренним образом [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для поиска проблем и исправить их, если это необходимо.  
  
### <a name="configure-monitoring-parameters-for-includesssmartbackupincludesss-smartbackup-mdmd"></a>Настройка параметров наблюдения для [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]  
 **Хранимую процедуру smart_admin.sp_set_parameter** системная хранимая процедура позволяет указать параметры мониторинга. В следующих разделах даны пошаговые инструкции по процедуре включения расширенных событий, а также по включению уведомления по электронной почте об ошибках и предупреждениях.  
  
 **Smart_admin.fn_get_parameter** функция может использоваться для получения текущей настройки определенного параметра или всех настроенных параметров. Если параметры не были настроены, функция не возвращает значения.  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте и вставьте следующий пример в окно запроса и нажмите кнопку **Выполнить**. Будет возвращена текущая конфигурация расширенных событий и уведомлений по электронной почте.  
  
```  
Use msdb  
Go  
SELECT * FROM smart_admin.fn_get_parameter (NULL)  
GO  
```  
  
 Дополнительные сведения см. в разделе [smart_admin.fn_get_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)  
  
### <a name="extended-events-for-monitoring"></a>Расширенные события для наблюдения  
 По умолчанию включены события Admin, Operational и Analytical. События административного канала наиболее важны и полезны при определении ошибок, требующих ручного вмешательства для решения проблемы. Возможно, необходимо включить операционные события и события отладки, однако следует иметь в виду, что эти события весьма подробны и могут потребовать фильтрации. В следующих процедурах описывается наблюдение за событиями, занесенными в журнал с помощью расширенных событий.  
  
> [!IMPORTANT]  
>  В отличие от расширенных событий для SQL Engine в [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] не поддерживаются сеансы расширенных событий. Системные хранимые процедуры и функции используются для взаимодействия с расширенными событиями. Кроме того, можно просматривать журнал расширенных событий из каталога журналов.  
  
##### <a name="to-configure-and-view-extended-events"></a>Настройка и просмотр расширенных событий  
  
1.  Чтобы просмотреть доступные каналы расширенных событий и их текущее состояние, выполните следующий запрос:  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     В выходных данных этого запроса отобразится параметр event_name, его доступность для настройки, а также будет показано, включен ли он в данный момент.  Дополнительные сведения см. в разделе [smart_admin.fn_get_current_xevent_settings &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql).  
  
2.  Чтобы включить события отладки, выполните следующий запрос:  
  
    ```  
    --  to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
     Дополнительные сведения о хранимой процедуре см. в разделе [хранимую процедуру smart_admin.sp_set_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql).  
  
3.  Чтобы просмотреть зарегистрированные события, выполните следующий запрос:  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
### <a name="aggregated-error-countshealth-status"></a>Суммарное количество ошибок или состояние работоспособности  
 **Smart_admin.fn_get_health_status** функция возвращает таблицу суммарного количества ошибок для каждой категории, который может использоваться для мониторинга состояния работоспособности [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Та же функция используется настроенным системой механизмом уведомления по электронной почте, который описывается далее в этом разделе.   
Эти суммарные значения можно использовать для контроля состояния работоспособности системы. Например, если столбец «number_ of_retention_loops» имеет значение 0 за 30 минут, то, возможно, управление хранением работает слишком долго или неправильно. Ненулевые столбцы ошибок могут означать неполадки, и для обнаружения проблемы следует проверить журналы расширенных событий. Кроме того, вызвать **smart_admin.sp_get_backup_diagnostics** хранимую процедуру, чтобы найти сведения об ошибке.  
  
### <a name="using-agent-notification-for-assessing-backup-status-and-health"></a>Использование уведомлений агента для оценки состояния и работоспособности резервного копирования  
 В состав [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] входит механизм уведомлений, который базируется на правилах управления SQL Server на основе политик.  
  
 **Предварительные условия.**  
  
-   Для работы этой функции необходим компонент Database Mail. Дополнительные сведения о включении компонента DB Mail для экземпляра SQL Server, см. в разделе [настроить компонент Database Mail](../relational-databases/database-mail/configure-database-mail.md).  
  
-   Чтобы использовать компонент Database Mail, необходимо задать свойства системы предупреждений агента SQL Server.  
  
 **Архитектура уведомлений:**  
  
-   **Управление на основе политик:** Для мониторинга работоспособности резервного копирования настраиваются две политики: **Смарт-политика работоспособности системы администратора**и **смарт-политика работоспособности действий пользователя с правами администратора**. Политика работоспособности системы Smart Admin оценивает критические ошибки, например отсутствие учетных данных SQL или неправильные данные, а также ошибки связи и сообщает о работоспособности системы. В таких случаях для исправления основной проблемы требуется выполнять действия вручную. Политика действий пользователя Smart Admin оценивает предупреждения, например о поврежденных резервных копиях и т. п.  Здесь может не потребоваться никаких действий, это просто предупреждение о событии. Предполагается, что подобные проблемы будет автоматически решать агент [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
-   **Агент SQL Server** задания: Уведомление выполняется с помощью задания агента SQL Server, три этапа. На первом этапе задания определяется, для чего настроен агент [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]: для базы данных или для экземпляра. При обнаружении [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] включена и настроена, она выполняется второй шаг: выполняет командлет PowerShell, который оценивает состояние работоспособности путем оценки политик управления на основе политик SQL Server. При обнаружении ошибки или предупреждения, он завершается ошибкой, которая затем запускает третий шаг: Третий шаг отправляет уведомление по электронной почте с отчетом ошибки или предупреждения.  Однако это задание агента SQL Server не включено по умолчанию. Чтобы включить задание уведомления по электронной почте, используйте **smart_admin.sp_set_backup_parameter** системной хранимой процедуры.  Следующая процедура описывает эти шаги более подробно.  
  
##### <a name="enabling-email-notification"></a>Включение уведомления по электронной почте  
  
1.  Если компонент Database Mail еще не настроен, выполните действия, описанные в [настроить компонент Database Mail](../relational-databases/database-mail/configure-database-mail.md).  
  
2.  Перевод базы данных в качестве почтовой системы для система предупреждений SQL Server. Щелкните правой кнопкой мыши **агента SQL Server**выберите **система предупреждений**, проверьте **Включить почтовый профиль** поле, выберите **компонента Database Mail** как  **Почтовая система**и выберите ранее созданный профиль электронной почты.  
  
3.  Запустите приведенный ниже запрос в окне запросов и укажите адрес электронной почты, на который должны отправляться уведомления.  
  
    ```  
    Use msdb  
    Go  
    EXEC smart_admin.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'  
  
    ```  
  
     Будет создано задание агента SQL Server, используемое для сбора сведений о состоянии работоспособности и отправки уведомлений при наличии ошибок или проблем резервного копирования.  
  
 Далее приведен образец скрипта для включения компонента DB Mail и отправки уведомления по электронной почте с помощью задания агента SQL Server  
  
```  
-- Prereq: Make sure that SQL Server service runs in a service account that has  
--  access to SMTP Server   
-- set SQL Server service account as domain account   
  
EXEC sp_configure 'show advanced', 1  
RECONFIGURE  
GO  
  
-- Enable DBMail  
EXEC sp_configure 'Database Mail XPs',1  
GO  
RECONFIGURE  
GO  
  
-- Configure DBMail  
DECLARE @emailid NVARCHAR(255)  
-- Note: change this email to your own email id  
SET @emailid = N'emailalias@mycompany.com'  
  
DECLARE @smtpserver NVARCHAR(255)  
SET @smtpserver = N'smtphost.domainname.com'  
  
DECLARE @mailprofile NVARCHAR(255)  
SET @mailprofile = N'my_profile'  
  
EXEC msdb.dbo.sysmail_add_account_sp @account_name=N'myaccount',  
                @email_address = @emailid,  
                @replyto_address = @emailid,  
                @mailserver_name = @smtpserver,  
                @use_default_credentials = 1  
  
EXEC msdb.dbo.sysmail_add_profile_sp @profile_name=@mailprofile  
EXEC msdb.dbo.sysmail_add_profileaccount_sp @profile_name=@mailprofile, @account_name=N'myaccount', @sequence_number=1  
  
-- Set SQL Agent to use DBMail profile  
EXEC msdb.dbo.sp_set_sqlagent_properties @databasemail_profile = @mailprofile  
  
-- Configure Notifications   
EXEC msdb.smart_admin.sp_set_parameter  
@parameter_name = 'SSMBackup2WANotificationEmailIds',  
@parameter_value = @emailid  
  
-- To test is you are receiving notifications  
-- delete few backup files from your storage container, Wait for 15 minutes & see if you get any email notification  
  
```  
  
### <a name="using-powershell-to-setup-custom-health-monitoring"></a>Настройка пользовательского наблюдения за работоспособностью с помощью PowerShell  
 **Test-SqlSmartAdmin** командлет можно использовать для создания пользовательского наблюдения за работоспособностью. Например, параметр уведомлений, описанный в предыдущем разделе, можно настроить на уровне экземпляра.  Если автоматическое резервное копирование с помощью [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] настроено в нескольких экземплярах SQL Server, командлет PowerShell можно использовать для создания скриптов для сбора сведений о состоянии и работоспособности сеансов резервного копирования для всех экземпляров.  
  
 **Test-SqlSmartAdmin** командлет оценивает ошибки и предупреждения, возвращаемые с помощью политик управления на основе политик SQL Server и отчетов среди свернутое состояние.  По умолчанию этот командлет использует системные политики. Чтобы включить пользовательскую политику, воспользуйтесь параметром `-AllowUserPolicies`.  
  
 Далее приведен образец скрипта PowerShell, который возвращает отчет об ошибках и предупреждениях на основе системных политик и любых политик, созданных пользователем.  
  
```  
$policyResults = get-sqlsmartadmin | test-sqlsmartadmin -AllowUserPolicies  
$policyResults.PolicyEvaluationDetails | select Name, Category, Expression, Result, Exception | fl  
  
```  
  
 Следующий скрипт возвращает подробный отчет об ошибках и предупреждениях для экземпляра по умолчанию.  
  
```  
PS C:\>PS SQLSERVER:\SQL\COMPUTER\DEFAULT> (get-sqlsmartadmin ).EnumHealthStatus()  
```  
  
### <a name="objects-in-msdb-database"></a>Объекты в базе данных MSDB  
 Это объекты, установленные для реализации функций MSDB. Они зарезервированы для внутреннего использования. Однако есть одна системная таблица, которые могут быть полезны при мониторинге состояние резервного копирования: smart_backup_files. Большая часть сведений, хранящихся в этой таблице, например Тип резервной копии, базы данных имя, во-первых и последний номер lsn, срок жизни копии, предоставляются с помощью системной функции [smart_admin.fn_available_backups &#40;Transact-SQL &#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql). Однако столбец состояния в таблице smart_backup_files, указывающий состояние файла резервной копии, через данную функцию недоступен. Далее приведен пример запроса, который можно использовать для получения некоторых сведений из системной таблицы, включая состояние.  
  
```  
USE msdb  
GO  
SELECT  
 database_name AS [Database Name]  
,backup_path AS [Backup Destination and File]  
,[Backup Type] =  
CASE backup_type  
WHEN 1 THEN 'FULL'  
WHEN 2 THEN 'LOG'  
END  
,[Backup Status] =  
CASE [status]  
WHEN 'A' THEN 'Available'  
WHEN 'B' THEN 'Copy In Progress'  
WHEN 'C' THEN 'Corrupted'  
WHEN 'D' THEN 'Deleted'  
WHEN 'F' THEN 'Copy Failed'  
WHEN 'U' THEN 'Unknown'  
END  
,first_lsn AS [First LSN]  
,last_lsn AS [Last LSN]  
,backup_start_date AS [Backup Start Time]  
,backup_finish_date AS [Backup Completion Time]  
,expiration_date AS [Backup Expiry Date/Time]  
FROM  
smart_backup_files;  
  
```  
  
 Далее дается подробное описание различных значений кода состояния.  
  
-   **Доступные - A:** Это обычный файл резервной копии. Резервное копирование выполнено, а также проверена доступность копии в хранилище Windows Azure.  
  
-   **Copy in Progress-B:** Это состояние не специально для баз данных группы доступности. Если [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] обнаружит разрыв в цепочке резервного копирования журнала, сначала будет сделана попытка определить операцию копирования, вызвавшую этот разрыв. При обнаружении файла резервной копии будет сделана попытка скопировать файл в хранилище Windows Azure. Данное состояние отображается при выполнении операции копирования.  
  
-   **Не удалось скопировать - F:** Как и Copy In Progress, это конкретных баз данных группы доступности. Если процесс копирования завершается ошибкой, состояние отмечается как F.  
  
-   **Поврежден - C:** Если [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] — не удалось проверить файл резервной копии в хранилище, выполнив команду RESTORE HEADER_ONLY даже после нескольких попыток, файл помечается как поврежденный. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] запланирует резервное копирование, чтобы поврежденный файл не привел к разрыву в цепочке резервного копирования.  
  
-   **Удалить — D:** Соответствующий файл не найден в хранилище Windows Azure. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] запланирует резервное копирование, если удаленный файл приведет к разрыву в цепочке резервного копирования.  
  
-   **Неизвестный - U:** Это состояние указывает, что [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] еще не удалось проверить наличие файла и его свойства в хранилище Windows Azure. При следующем запуске процесса, что обычно происходит через каждые 15 минут, это состояние будет обновлено.  
  
  
