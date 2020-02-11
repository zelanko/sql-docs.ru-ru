---
title: Мониторинг SQL Server управляемого резервного копирования в Azure | Документация Майкрософт
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
ms.openlocfilehash: 25e45e5877d528d1f01fe8695d8575466991c381
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "72798036"
---
# <a name="monitor-sql-server-managed-backup-to-azure"></a>Мониторинг управляемого резервного копирования SQL Server в Azure
  В [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] предусмотрены встроенные меры по определению неполадок и ошибок в процессе резервного копирования, а также действия по исправлению, когда это возможно.  Однако есть некоторые решения, для которых требуется участие пользователя. В этом разделе описаны средства, с помощью которых можно определять общее состояние исправности резервных копий, а также определять любые ошибки, которые требуют устранения.  
  
## <a name="overview-of-includess_smartbackupincludesss-smartbackup-mdmd-built-in-debugging"></a>Обзор встроенной отладки [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]  
 
  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] периодически просматривает запланированные сеансы резервного копирования и пытается повторно запланировать те, что завершились с ошибками. Он периодически опрашивает учетную запись хранения, чтобы найти разрыв в цепочке журналов, влияющий на восстанавливаемость базы данных, и планирует соответствующим образом новое резервное копирование. Он также учитывает политики регулирования Azure и имеет механизмы для управления несколькими резервными копиями баз данных. Служба [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] использует расширенные события для отслеживания всех действий. Далее перечислены каналы расширенных событий, используемые агентом [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]: Admin, Operational, Analytical и Debug. События, относящиеся к категории Admin, обычно связаны с ошибками, требуют вмешательства пользователя и включены по умолчанию. События Analytical также включены по умолчанию, но обычно не связаны с ошибками, требующими вмешательства пользователя. События операций обычно информационные. Например, рабочие события включают в себя планирование резервного копирования, успешное завершение резервного копирования и т. д. Отладка является наиболее подробным и используется для внутренних целей, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] чтобы определить проблемы и исправить их при необходимости.  
  
### <a name="configure-monitoring-parameters-for-includess_smartbackupincludesss-smartbackup-mdmd"></a>Настройка параметров наблюдения для [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]  
 Системная хранимая процедура **smart_admin. sp_set_parameter** позволяет указать параметры мониторинга. В следующих разделах даны пошаговые инструкции по процедуре включения расширенных событий, а также по включению уведомления по электронной почте об ошибках и предупреждениях.  
  
 Функцию **smart_admin. fn_get_parameter** можно использовать для получения текущей настройки для конкретного параметра или всех настроенных параметров. Если параметры не были настроены, функция не возвращает значения.  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте и вставьте следующий пример в окно запроса и нажмите кнопку **Выполнить**. Будет возвращена текущая конфигурация расширенных событий и уведомлений по электронной почте.  
  
```sql
Use msdb  
Go  
SELECT * FROM smart_admin.fn_get_parameter (NULL)  
GO  
```  
  
 Дополнительные сведения см. в разделе [smart_admin. fn_get_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)  
  
### <a name="extended-events-for-monitoring"></a>Расширенные события для наблюдения  
 По умолчанию включены события Admin, Operational и Analytical. События административного канала наиболее важны и полезны при определении ошибок, требующих ручного вмешательства для решения проблемы. Возможно, необходимо включить операционные события и события отладки, однако следует иметь в виду, что эти события весьма подробны и могут потребовать фильтрации. В следующих процедурах описывается наблюдение за событиями, занесенными в журнал с помощью расширенных событий.  
  
> [!IMPORTANT]  
>  В отличие от расширенных событий для SQL Engine в [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] не поддерживаются сеансы расширенных событий. Системные хранимые процедуры и функции используются для взаимодействия с расширенными событиями. Кроме того, можно просматривать журнал расширенных событий из каталога журналов.  
  
##### <a name="to-configure-and-view-extended-events"></a>Настройка и просмотр расширенных событий  
  
1.  Чтобы просмотреть доступные каналы расширенных событий и их текущее состояние, выполните следующий запрос:  
  
    ```sql
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     В выходных данных этого запроса отобразится параметр event_name, его доступность для настройки, а также будет показано, включен ли он в данный момент.  Дополнительные сведения см. в разделе [smart_admin. fn_get_current_xevent_settings &#40;&#41;Transact-SQL ](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql).  
  
2.  Чтобы включить события отладки, выполните следующий запрос:  
  
    ```sql
    --  to enable debug events  
    Use msdb;  
    GO 
    EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
    ```  
  
     Дополнительные сведения о хранимой процедуре см. в разделе [smart_admin. sp_set_parameter &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql).  
  
3.  Чтобы просмотреть зарегистрированные события, выполните следующий запрос:  
  
    ```sql
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;
    ```  
  
    ```sql
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
 Функция **smart_admin. fn_get_health_status** возвращает таблицу агрегированных счетчиков ошибок для каждой категории, которая может использоваться для наблюдения за состоянием работоспособности [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Та же функция используется настроенным системой механизмом уведомления по электронной почте, который описывается далее в этом разделе.   
Эти суммарные значения можно использовать для контроля состояния работоспособности системы. Например, если столбец «number_ of_retention_loops» имеет значение 0 за 30 минут, то, возможно, управление хранением работает слишком долго или неправильно. Ненулевые столбцы ошибок могут означать неполадки, и для обнаружения проблемы следует проверить журналы расширенных событий. Кроме того, для поиска сведений об ошибке вызовите хранимую процедуру **smart_admin. sp_get_backup_diagnostics** .  
  
### <a name="using-agent-notification-for-assessing-backup-status-and-health"></a>Использование уведомлений агента для оценки состояния и работоспособности резервного копирования  
 В состав [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] входит механизм уведомлений, который базируется на правилах управления SQL Server на основе политик.  
  
 **Требований**  
  
-   Для работы этой функции необходим компонент Database Mail. Дополнительные сведения о включении компонента Database Mail для экземпляра SQL Server см. в разделе [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).  
  
-   Чтобы использовать компонент Database Mail, необходимо задать свойства системы предупреждений агента SQL Server.  
  
 **Архитектура уведомлений**  
  
-   **Управление на основе политик:** Установлены две политики для наблюдения за работоспособностью резервного копирования: **политика работоспособности системы интеллектуального администрирования**и **Политика исправности пользователя интеллектуального администратора**. Политика работоспособности системы Smart Admin оценивает критические ошибки, например отсутствие учетных данных SQL или неправильные данные, а также ошибки связи и сообщает о работоспособности системы. В таких случаях для исправления основной проблемы требуется выполнять действия вручную. Политика действий пользователя Smart Admin оценивает предупреждения, например о поврежденных резервных копиях и т. п.  Здесь может не потребоваться никаких действий, это просто предупреждение о событии. Предполагается, что подобные проблемы будет автоматически решать агент [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
-   **Агент SQL Server** Задание. Уведомление выполняется с помощью задания агент SQL Server, которое содержит три шага задания. На первом этапе задания определяется, для чего настроен агент [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]: для базы данных или для экземпляра. Если обнаруживается [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] включенный и настроенный, он выполняет второй шаг: выполняет командлет PowerShell, который оценивает состояние работоспособности, оценивая политики управления на основе политик SQL Server. Если обнаруживается ошибка или предупреждение, происходит сбой, после чего запускается третий шаг: Третий шаг отправляет уведомление по электронной почте с отчетом об ошибках и предупреждениях.  Однако это задание агента SQL Server не включено по умолчанию. Чтобы включить задание уведомления по электронной почте, используйте системную хранимую процедуру **smart_admin. sp_set_backup_parameter** .  Следующая процедура описывает эти шаги более подробно.  
  
##### <a name="enabling-email-notification"></a>Включение уведомления по электронной почте  
  
1.  Если Database Mail еще не настроена, выполните действия, описанные в разделе [настройка Database Mail](../relational-databases/database-mail/configure-database-mail.md).  
  
2.  Установите базу данных в качестве почтовой системы для SQL Server системы предупреждений: щелкните правой кнопкой мыши **Агент SQL Server**, выберите **система предупреждений**, установите флажок **включить почтовый профиль** , выберите пункт **Database Mail** в качестве **почтовой системы**и выберите ранее созданный профиль электронной почты.  
  
3.  Запустите приведенный ниже запрос в окне запросов и укажите адрес электронной почты, на который должны отправляться уведомления.  
  
    ```sql
    Use msdb  
    Go  
    EXEC smart_admin.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'
    ```  
  
     Будет создано задание агента SQL Server, используемое для сбора сведений о состоянии работоспособности и отправки уведомлений при наличии ошибок или проблем резервного копирования.  
  
 Далее приведен образец скрипта для включения компонента DB Mail и отправки уведомления по электронной почте с помощью задания агента SQL Server  
  
```sql
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
 Командлет **Test-SqlSmartAdmin** можно использовать для создания настраиваемого мониторинга работоспособности. Например, параметр уведомлений, описанный в предыдущем разделе, можно настроить на уровне экземпляра.  Если автоматическое резервное копирование с помощью [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] настроено в нескольких экземплярах SQL Server, командлет PowerShell можно использовать для создания скриптов для сбора сведений о состоянии и работоспособности сеансов резервного копирования для всех экземпляров.  
  
 Командлет **Test-SqlSmartAdmin** оценивает ошибки и предупреждения, возвращаемые политиками управления на основе политики SQL Server и выводит сведенное состояние.  По умолчанию этот командлет использует системные политики. Чтобы включить пользовательскую политику, воспользуйтесь параметром `-AllowUserPolicies`.  
  
 Далее приведен образец скрипта PowerShell, который возвращает отчет об ошибках и предупреждениях на основе системных политик и любых политик, созданных пользователем.  
  
```powershell
$policyResults = Get-SqlSmartAdmin | Test-SqlSmartAdmin -AllowUserPolicies  
$policyResults.PolicyEvaluationDetails | Select Name, Category, Expression, Result, Exception | fl
```  
  
 Следующий скрипт возвращает подробный отчет об ошибках и предупреждениях для экземпляра по умолчанию`\SQL\COMPUTER\DEFAULT`():  
  
```powershell
(Get-SqlSmartAdmin ).EnumHealthStatus()  
```  
  
### <a name="objects-in-msdb-database"></a>Объекты в базе данных MSDB  
 Это объекты, установленные для реализации функций MSDB. Они зарезервированы для внутреннего использования. Однако существует одна системная таблица, которая может быть полезна при наблюдении за состоянием резервного копирования: smart_backup_files. Большая часть информации, хранящейся в этой таблице, относится к мониторингу, например к типу резервной копии, имени базы данных, первому и последнему номеру LSN, даты истечения срока действия резервной копии предоставляются через системную функцию [smart_admin. fn_available_backups &#40;&#41;Transact-SQL ](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql). Однако столбец состояния в таблице smart_backup_files, указывающий состояние файла резервной копии, через данную функцию недоступен. Далее приведен пример запроса, который можно использовать для получения некоторых сведений из системной таблицы, включая состояние.  
  
```sql
USE msdb  
GO  
SELECT  
 database_name AS [Database Name] ,backup_path AS [Backup Destination and File]  
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
  
-   **Доступно:** Это стандартный файл резервной копии. Резервное копирование завершено, а также проверено, что она доступна в службе хранилища Azure.  
  
-   **Копирование выполняется — б:** Это состояние предназначено для баз данных групп доступности. Если [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] обнаружит разрыв в цепочке резервного копирования журнала, сначала будет сделана попытка определить операцию копирования, вызвавшую этот разрыв. При поиске файла резервной копии он пытается скопировать файл в службу хранилища Azure. Данное состояние отображается при выполнении операции копирования.  
  
-   **Сбой копирования — F:** Как и в процессе копирования, это конкретные базы данных групп доступности t. Если процесс копирования завершается ошибкой, состояние отмечается как F.  
  
-   **Повреждено — C:** Если [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] не удается проверить файл резервной копии в хранилище, выполнив команду restore HEADER_ONLY, даже после нескольких попыток, этот файл помечается как поврежденный. 
  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] запланирует резервное копирование, чтобы поврежденный файл не привел к разрыву в цепочке резервного копирования.  
  
-   **Удалено-D:** Соответствующий файл не найден в службе хранилища Azure. 
  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] запланирует резервное копирование, если удаленный файл приведет к разрыву в цепочке резервного копирования.  
  
-   **Неизвестный-U:** Это состояние указывает, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] что еще не удалось проверить существование файла и его свойства в службе хранилища Azure. При следующем запуске процесса, что обычно происходит через каждые 15 минут, это состояние будет обновлено.  
