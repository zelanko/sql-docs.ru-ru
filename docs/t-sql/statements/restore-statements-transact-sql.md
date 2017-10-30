---
title: "RESTORE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RESTORE DATABASE
- RESTORE_TSQL
- RESTORE_DATABASE_TSQL
- RESTORE
- RESTORE_LOG_TSQL
- RESTORE LOG
dev_langs:
- TSQL
helpviewer_keywords:
- RESTORE DATABASE, see RESTORE statement
- full backups [SQL Server]
- RECOVERY option
- database snapshots [SQL Server], reverting to
- STOPAT syntax
- differential backups, RESTORE statement
- point in time recovery [SQL Server]
- restoring [SQL Server]
- NORECOVERY option
- online restores [SQL Server], RESTORE statement
- moving databases
- RESTORE statement, syntax
- cross-platform restores
- restoring databases [SQL Server], options
- RESTORE statement
- snapshots [SQL Server database snapshots], reverting to
- reverting database snapshots
- transaction log backups [SQL Server], RESTORE statement
- RESTORE LOG, see RESTORE statement
ms.assetid: 877ecd57-3f2e-4237-890a-08f16e944ef1
caps.latest.revision: 248
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: e233de35336d5246c439c5dfb7b934cd2469b92c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---
# <a name="restore-statements-transact-sql"></a>ВОССТАНОВЛЕНИЕ инструкции (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Восстанавливает резервные копии, выполненные при помощи команды BACKUP. Эта команда позволяет выполнить следующие сценарии восстановления.  
  
-   Восстановить базу данных из полной резервной копии (полное восстановление).  
  
-   Восстановить часть базы данных (частичное восстановление).  
  
-   Восстановить в базе данных определенные файлы или файловые группы (восстановление файлов).  
  
-   Восстановить в базе данных определенные страницы (восстановление страниц).  
  
-   Восстановить в базе данных журнал транзакций (восстановление журнала транзакций).  
  
-   Вернуть базу данных к моменту времени, на который был выполнен моментальный снимок базы данных.  
  
 Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сценариях восстановления см. в разделе [восстановления и восстановления Обзор &#40; SQL Server &#41; ](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md).  Дополнительные сведения об описаниях аргументов см. в разделе [аргументы инструкции RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).   При восстановлении базы данных из другого экземпляра примите во внимание сведения из раздела [Управление метаданными при обеспечении доступности базы данных на другом экземпляре сервера (SQL Server)](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).
  
> **Примечание:** Дополнительные сведения о восстановлении из службы хранилища больших двоичных объектов Windows Azure см. в разделе [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
--To Restore an Entire Database from a Full database backup (a Complete Restore):  
RESTORE DATABASE { database_name | @database_name_var }   
 [ FROM <backup_device> [ ,...n ] ]  
 [ WITH   
   {  
    [ RECOVERY | NORECOVERY | STANDBY =   
        {standby_file_name | @standby_file_name_var }   
       ]  
   | ,  <general_WITH_options> [ ,...n ]  
   | , <replication_WITH_option>  
   | , <change_data_capture_WITH_option>  
   | , <FILESTREAM_WITH_option>  
   | , <service_broker_WITH options>   
   | , \<point_in_time_WITH_options—RESTORE_DATABASE>   
   } [ ,...n ]  
 ]  
[;]  
  
--To perform the first step of the initial restore sequence  
-- of a piecemeal restore:  
RESTORE DATABASE { database_name | @database_name_var }   
   <files_or_filegroups> [ ,...n ]  
 [ FROM <backup_device> [ ,...n ] ]   
   WITH   
      PARTIAL, NORECOVERY   
      [  , <general_WITH_options> [ ,...n ]   
       | , \<point_in_time_WITH_options—RESTORE_DATABASE>   
      ] [ ,...n ]   
[;]  
  
--To Restore Specific Files or Filegroups:   
RESTORE DATABASE { database_name | @database_name_var }   
   <file_or_filegroup> [ ,...n ]  
 [ FROM <backup_device> [ ,...n ] ]   
   WITH   
   {  
      [ RECOVERY | NORECOVERY ]  
      [ , <general_WITH_options> [ ,...n ] ]  
   } [ ,...n ]   
[;]  
  
--To Restore Specific Pages:   
RESTORE DATABASE { database_name | @database_name_var }   
   PAGE = 'file:page [ ,...n ]'   
 [ , <file_or_filegroups> ] [ ,...n ]  
 [ FROM <backup_device> [ ,...n ] ]   
   WITH   
       NORECOVERY     
      [ , <general_WITH_options> [ ,...n ] ]  
[;]  
  
--To Restore a Transaction Log:  
RESTORE LOG { database_name | @database_name_var }   
 [ <file_or_filegroup_or_pages> [ ,...n ] ]  
 [ FROM <backup_device> [ ,...n ] ]   
 [ WITH   
   {  
     [ RECOVERY | NORECOVERY | STANDBY =   
        {standby_file_name | @standby_file_name_var }   
       ]  
    | ,  <general_WITH_options> [ ,...n ]  
    | , <replication_WITH_option>  
    | , \<point_in_time_WITH_options—RESTORE_LOG>   
   } [ ,...n ]  
 ]   
[;]  
  
--To Revert a Database to a Database Snapshot:     
RESTORE DATABASE { database_name | @database_name_var }   
FROM DATABASE_SNAPSHOT = database_snapshot_name   
  
<backup_device>::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
 | { DISK | TAPE | URL } = { 'physical_backup_device_name' |  
      @physical_backup_device_name_var }   
}   
Note: URL is the format used to specify the location and the file name for the Windows Azure Blob. Although Windows Azure storage is a service, the implementation is similar to disk and tape to allow for a consistent and seemless restore experince for all the three devices.  
<files_or_filegroups>::=   
{   
   FILE = { logical_file_name_in_backup | @logical_file_name_in_backup_var }   
 | FILEGROUP = { logical_filegroup_name | @logical_filegroup_name_var }   
 | READ_WRITE_FILEGROUPS  
}   
  
<general_WITH_options> [ ,...n ]::=   
--Restore Operation Options  
   MOVE 'logical_file_name_in_backup' TO 'operating_system_file_name'   
          [ ,...n ]   
 | REPLACE   
 | RESTART   
 | RESTRICTED_USER  | CREDENTIAL  
  
--Backup Set Options  
 | FILE = { backup_set_file_number | @backup_set_file_number }   
 | PASSWORD = { password | @password_variable }   
  
--Media Set Options  
 | MEDIANAME = { media_name | @media_name_variable }   
 | MEDIAPASSWORD = { mediapassword | @mediapassword_variable }   
 | BLOCKSIZE = { blocksize | @blocksize_variable }   
  
--Data Transfer Options  
 | BUFFERCOUNT = { buffercount | @buffercount_variable }   
 | MAXTRANSFERSIZE = { maxtransfersize | @maxtransfersize_variable }  
  
--Error Management Options  
 | { CHECKSUM | NO_CHECKSUM }   
 | { STOP_ON_ERROR | CONTINUE_AFTER_ERROR }   
  
--Monitoring Options  
 | STATS [ = percentage ]   
  
--Tape Options  
 | { REWIND | NOREWIND }   
 | { UNLOAD | NOUNLOAD }   
  
<replication_WITH_option>::=  
 | KEEP_REPLICATION   
  
<change_data_capture_WITH_option>::=  
 | KEEP_CDC  
  
<FILESTREAM_WITH_option>::=  
 | FILESTREAM ( DIRECTORY_NAME = directory_name )  
  
<service_broker_WITH_options>::=   
 | ENABLE_BROKER   
 | ERROR_BROKER_CONVERSATIONS   
 | NEW_BROKER  
  
\<point_in_time_WITH_options—RESTORE_DATABASE>::=   
 | {  
   STOPAT = { 'datetime'| @datetime_var }   
 | STOPATMARK = 'lsn:lsn_number'  
                 [ AFTER 'datetime']   
 | STOPBEFOREMARK = 'lsn:lsn_number'  
                 [ AFTER 'datetime']   
   }   
  
\<point_in_time_WITH_options—RESTORE_LOG>::=   
 | {  
   STOPAT = { 'datetime'| @datetime_var }   
 | STOPATMARK = { 'mark_name' | 'lsn:lsn_number' }  
                 [ AFTER 'datetime']   
 | STOPBEFOREMARK = { 'mark_name' | 'lsn:lsn_number' }  
                 [ AFTER 'datetime']   
   }  
  
```  
  
## <a name="arguments"></a>Аргументы  
 Описания аргументов см. в разделе [аргументы инструкции RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="about-restore-scenarios"></a>Сведения о сценариях восстановления  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает различные сценарии восстановления.  
  
-   полное восстановление базы данных  
  
     Восстанавливает всю базу данных, начиная с полной резервной копии, за которой может последовать восстановление из копии разностной резервной копии базы данных (и резервных копий журналов). Дополнительные сведения см. в разделе [Выполнение полного восстановления базы данных (простая модель восстановления)](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md) или [Выполнение полного восстановления базы данных (модель полного восстановления)](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md).  
  
-   Восстановление файлов  
  
     Восстанавливается файл или файловая группа в базе данных, содержащей несколько файловых групп. Следует заметить, что при использовании простой модели восстановления файл должен принадлежать к файловой группе, находящейся в режиме только для чтения. После полного восстановления файлов может быть восстановлена разностная резервная копия файлов. Дополнительные сведения см. в разделе [восстановление файлов &#40; Модель полного восстановления &#41; ](../../relational-databases/backup-restore/file-restores-full-recovery-model.md) и [файла восстановления &#40; Простая модель восстановления &#41; ](../../relational-databases/backup-restore/file-restores-simple-recovery-model.md).  
  
-   Восстановление страницы  
  
     Производится восстановление отдельных страниц. Восстановление страницы возможно только в моделях полного восстановления и восстановления с неполным протоколированием. Дополнительные сведения см. в разделе [Восстановление страниц (SQL Server)](../../relational-databases/backup-restore/restore-pages-sql-server.md).  
  
-   Поэтапное восстановление  
  
     Восстановление базы данных производится по этапам, начиная с первичной файловой группы и одной или нескольких вторичных файловых групп. Поэтапное восстановление начинается с инструкции RESTORE DATABASE с параметром PARTIAL и указания одной или нескольких восстанавливаемых вторичных файловых групп. Дополнительные сведения см. в разделе [Поэтапное восстановление (SQL Server)](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md).  
  
-   Только восстановление  
  
     Данные восстанавливаются в том случае, если они уже согласованы с базой данных и необходимо только сделать их доступными. Дополнительные сведения см. в разделе [Восстановление базы данных без восстановления данных (Transact-SQL)](../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md).  
  
-   Восстановление журнала транзакций  
  
     В моделях полного восстановления и восстановления с неполным протоколированием восстановление резервных копий журналов необходимо для достижения необходимой точки восстановления. Дополнительные сведения о восстановлении резервных копий журналов см. в разделе [применение резервных копий журнала транзакций &#40; SQL Server &#41; ](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md).  
  
-   Подготовка базы данных доступности для группы доступности Always On  
  
     Дополнительные сведения см. в разделе [Подготовка базы данных-получателя для присоединения к группе доступности вручную (SQL Server)](../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
-   Подготовка зеркальной базы данных к зеркальному отображению  
  
     Дополнительные сведения см. в статье [Подготовка зеркальной базы данных к зеркальному отображению (SQL Server)](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md).  
  
-   Восстановление в сети  
  
    > **Примечание:** оперативное восстановление допускается только в выпуске Enterprise edition [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Если поддерживается оперативное восстановление и база данных доступна в сети, автоматически выполняется оперативное восстановление файлов и страниц. Кроме того, после начального этапа поэтапного восстановления выполняется восстановление вторичной файловой группы.  
  
    > **Примечание:** оперативное восстановление может включать в себя [отложенных транзакций](../../relational-databases/backup-restore/deferred-transactions-sql-server.md).  
  
     Дополнительные сведения см. в разделе [оперативное восстановление &#40; SQL Server &#41; ](../../relational-databases/backup-restore/online-restore-sql-server.md).  
  
## <a name="additional-considerations-about-restore-options"></a>Дополнительные сведения о параметрах инструкции RESTORE  
  
### <a name="discontinued-restore-keywords"></a>Неподдерживаемые ключевые слова инструкции RESTORE  
 В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] следующие ключевые слова больше не поддерживаются.  
  
|Неподдерживаемое ключевое слово|Заменены на...|Пример заменяющего ключевого слова|  
|--------------------------|------------------|------------------------------------|  
|LOAD|RESTORE|`RESTORE DATABASE`|  
|TRANSACTION|LOG|`RESTORE LOG`|  
|DBO_ONLY|RESTRICTED_USER|`RESTORE DATABASE ... WITH RESTRICTED_USER`|  
  
### <a name="restore-log"></a>RESTORE LOG  
 Инструкция RESTORE LOG может включать список файлов, создаваемых во время наката. Эта возможность используется, если резервная копия журналов содержит журнальные записи, произведенные во время добавления файла в базу данных.  
  
> **Примечание:** для базы данных с использованием модели восстановления с неполным протоколированием или полной, в большинстве случаев необходимо резервное копирование заключительного фрагмента журнала перед восстановлением базы данных. Восстановление базы данных без создания резервной копии заключительного фрагмента журнала приведет к ошибке, если инструкция RESTORE DATABASE не содержит предложение WITH REPLACE или WITH STOPAT, в котором должно указываться время или транзакция, выполняемая после завершения резервного копирования данных. Дополнительные сведения о резервных копиях заключительного фрагмента журнала см. в разделе [Резервные копии заключительного фрагмента журнала (SQL Server)](../../relational-databases/backup-restore/tail-log-backups-sql-server.md).  
  
### <a name="comparison-of-recovery-and-norecovery"></a>Сравнение параметров RECOVERY и NORECOVERY  
 Откат контролируется инструкцией RESTORE при помощи параметров [ RECOVERY | NORECOVERY ].  
  
-   Параметр NORECOVERY указывает на то, что откат не производится. Это позволяет продолжать накат при помощи следующей инструкции в последовательности.  
  
     В этом случае последовательность восстановления может восстановить другие резервные копии и выполнить их накат.  
  
-   Параметр RECOVERY (параметр по умолчанию) указывает на то, что откат должен быть выполнен после завершения наката для текущей резервной копии.  
  
     Восстановление базы данных требует, чтобы весь набор восстанавливаемых данных ( *набор данных наката*) согласован с базой данных. Если набор данных наката, необходимый для согласования с базой данных, достаточно велик и указан параметр RECOVERY, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] формирует ошибку.  
  
## <a name="compatibility-support"></a>Поддержка совместимости  
 Резервные копии **master**, **модель** и **msdb** , созданные с помощью более ранней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может быть восстановлена на [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
> **Примечание:** нет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] восстановить в более ранней версии резервной копии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] от версии, на котором была создана резервная копия.  
  
 В каждой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется путь по умолчанию, отличный от пути в предыдущих версиях. Поэтому, чтобы восстановить из резервной копии базу данных, созданную в расположении по умолчанию для архивов предыдущих версий, необходимо использовать параметр MOVE. Сведения о новом пути по умолчанию см. в разделе [расположения файлов по умолчанию и именованных экземпляров SQL Server](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md).  
  
 Если восстановить базу данных предыдущей версии до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], то эта база данных автоматически обновится. Как правило, база данных сразу становится доступной. Но если база данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] содержит полнотекстовые индексы, при обновлении будет произведен их импорт, сброс или повторное создание в зависимости от установленного значения свойства сервера  **upgrade_option** . Если при обновлении выбран режим импорта (**upgrade_option** = 2) или перестроения (**upgrade_option** = 0), полнотекстовые индексы во время обновления будут недоступны. В зависимости от объема индексируемых данных процесс импорта может занять несколько часов, а перестроение — в несколько (до десяти) раз больше. Обратите внимание, что если для обновления выбран режим «Импортировать», а полнотекстовый каталог недоступен, то связанные с ним полнотекстовые индексы будут перестроены. Чтобы изменить значение свойства сервера **upgrade_option** , следует использовать процедуру [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md).  
  
 При первом присоединении базы данных к новому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или ее восстановлении копия главного ключа базы данных (зашифрованная главным ключом службы) еще не хранится на сервере. Необходимо расшифровать главный ключ базы данных с помощью инструкции **OPEN MASTER KEY** . Как только главный ключ базы данных будет расшифрован, появится возможность разрешить автоматическую расшифровку в будущем с помощью инструкции **ALTER MASTER KEY REGENERATE** , чтобы оставить на сервере копию главного ключа базы данных, зашифрованного с помощью главного ключа службы. После обновления базы данных с переходом от более ранней версии главный ключ базы данных должен быть создан повторно для использования нового алгоритма шифрования AES. Дополнительные сведения о повторном создании главного ключа базы данных см. в статье [ALTER MASTER KEY (Transact-SQL)](../../t-sql/statements/alter-master-key-transact-sql.md). Время, необходимое для повторного создания главного ключа базы данных с обновлением до алгоритма шифрования AES, зависит от числа объектов, защищаемых главным ключом базы данных. Повторное создание главного ключа базы данных с обновлением до алгоритма шифрования AES необходимо произвести только один раз. Это никак не повлияет на последующие операции повторного создания, выполняемые в соответствии со стратегией смены ключей.  
  
## <a name="general-remarks"></a>Общие замечания  
 Во время автономного восстановления, если указанная база данных используется, функция RESTORE после короткой задержки принудительно отключает пользователей. Для восстановления в режиме «в сети» непервичной файловой группы база данных может продолжать использоваться, за исключением тех случаев, когда восстанавливаемая файловая группа переводится в режим вне сети. Данные в указанной базе данных заменяются восстановленными данными.  
  
 Дополнительные сведения о восстановлении базы данных см. в разделе [восстановления и восстановления Обзор &#40; SQL Server &#41; ](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md).  
  
 Операции восстановления между несколькими платформами, даже между процессорами различных типов, могут выполняться, если параметры сортировки базы данных поддерживаются операционной системой.  
  
 После возникновения ошибки инструкция RESTORE может быть запущена вновь. Кроме того, можно указать, чтобы, несмотря на ошибки, инструкция RESTORE продолжала работу и восстановила как можно большее количество данных (см. параметр CONTINUE_AFTER_ERROR).  
  
 Инструкция RESTORE недопустима в явной или неявной транзакции.  
  
 Восстановление поврежденной **master** базы данных выполняется с помощью специальной процедуры. Дополнительные сведения см. в разделе [Резервное копирование и восстановление системных баз данных (SQL Server)](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
 Восстановление базы данных из копии удаляет кэш планов для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Очистка кэша планов становится причиной перекомпиляции всех последующих планов выполнения и приводит к непредвиденному временному снижению производительности обработки запросов. Для каждого удаленного хранилища кэша в кэше планов журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит следующее информационное сообщение: «[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил %d экземпляров, записанных на диск хранилищ кэша для хранилища кэша "%s" (части кэша планов) в результате операций по обслуживанию или изменению конфигурации базы данных». Это сообщение добавляется в журнал каждые пять минут при сбросе кэша в течение этого интервала времени.  
  
 Чтобы восстановить базу данных доступности, сначала восстановите базу данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а затем добавьте базу данных в группу доступности.  
  
## <a name="interoperability"></a>Совместимость  
  
### <a name="database-settings-and-restoring"></a>Настройка базы данных и восстановление  
 Во время восстановления большинство параметров базы данных, устанавливаемых при помощи инструкции ALTER DATABASE, сбрасывается в значения, в которых они находились в конце резервного копирования.  
  
 Однако использование параметра WITH RESTRICTED_USER переопределяет этот режим работы для настройки параметра доступа пользователя. Эта настройка всегда сохраняется, если инструкция RESTORE включает параметр WITH RESTRICTED_USER.  
  
### <a name="restoring-an-encrypted-database"></a>Восстановление зашифрованной базы данных  
 Чтобы восстановить зашифрованную базу данных, необходимо иметь доступ к сертификату или асимметричному ключу, который использовался для шифрования базы данных. Без сертификата или асимметричного ключа восстановить базу данных нельзя. Поэтому сертификат, используемый для шифрования ключа шифрования базы данных, должен храниться в течение всего времени, пока есть необходимость в резервной копии. Дополнительные сведения см. в статье [SQL Server Certificates and Asymmetric Keys](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  
  
### <a name="restoring-a-database-enabled-for-vardecimal-storage"></a>Восстановление базы данных с включенным форматом хранения vardecimal  
 Резервное копирование и восстановление правильно работают с **vardecimal** формат хранения. Дополнительные сведения о **vardecimal** формата хранения в разделе [sp_db_vardecimal_storage_format &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md).  
  
### <a name="restore-full-text-data"></a>Восстановление полнотекстовых данных  
 Во время полного восстановления полнотекстовые данные восстанавливаются вместе с другими данными базы данных. С помощью обычного синтаксиса `RESTORE DATABASE database_name FROM backup_device` полнотекстовые файлы восстанавливаются как часть файлов базы данных.  
  
 Инструкция RESTORE может также использоваться для восстановления в разные расположения, для разностного восстановления, восстановления файлов и файловых групп, а также для восстановления файлов и файловых групп полнотекстовых данных. Кроме того, инструкция RESTORE может восстанавливать как полнотекстовые файлы, так и файлы с данными базы данных.  
  
> **Примечание:** импортированные полнотекстовые каталоги из [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] по-прежнему рассматриваются как файлы базы данных. Для них остается применимой процедура [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] по резервному копированию полнотекстовых каталогов, за исключением того, что более нет необходимости использовать паузу и возобновление в процессе выполнения резервного копирования. Дополнительные сведения см. в разделе [резервное копирование и восстановление полнотекстовых каталогов](http://go.microsoft.com/fwlink/?LinkId=107381).  
  
## <a name="metadata"></a>Метаданные  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает таблицы журналов резервного копирования и восстановления, в которые заносятся данные слежения за резервным копированием и восстановлением для каждого экземпляра сервера. При выполнении восстановления таблицы журнала резервного копирования также изменяются. Сведения об этих таблицах см. в разделе [журнал резервного копирования и сведения о заголовке &#40; SQL Server &#41; ](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md).  
  
##  <a name="REPLACEoption"></a>Влияние параметра REPLACE  
 Параметр REPLACE должен использоваться редко и после тщательного анализа. Восстановление обычно не допускает случайной перезаписи базы данных другой базой данных. Если указанная в инструкции RESTORE база данных уже существует на текущем сервере, а идентификатор GUID семейства для заданной базы данных отличается от идентификатора GUID семейства для базы данных, записанного в резервном наборе данных, то ее восстановление не будет выполнено. Это является важной защитной мерой.  
  
 Параметр REPLACE отменяет несколько важных проверок, обычно выполняемых операцией восстановления. Отменяются следующие проверки.  
  
-   Проверка на восстановление поверх существующей базы данных резервной копии, созданной для другой базы данных.  
  
     При использовании параметра REPLACE при восстановлении можно записать данные поверх существующей базы данных независимо от того, какие базы данных содержатся в резервном наборе данных, даже если указанное имя данных отличается от записанного в резервном наборе. Это может привести к случайной перезаписи поверх базы данных другой базы данных.  
  
-   Проверка на восстановление базы данных, использующей модель полного восстановления или модель восстановления с неполным протоколированием, для которой не была создана резервная копия заключительного фрагмента журнала, и не был применен параметр STOPAT.  
  
     При использовании параметра REPLACE возможна потеря зафиксированных данных, поскольку последние записанные в журнал данные еще не были скопированы в резервную копию.  
  
-   Перезапись существующих файлов.  
  
     Проверка на перезапись существующих файлов неверного типа (например XLS-файлов) или файлов, используемых другой базой данных, в данный момент находящейся не в режиме в сети. Возможна случайная потеря данных в случае перезаписи существующих файлов, несмотря на то, что восстановленная база данных будет полной.  
  
## <a name="redoing-a-restore"></a>Повторное восстановление  
 Отменить результаты восстановления невозможно, однако можно отменить результаты копирования данных и произвести накат для каждого файла по отдельности. Для перезапуска восстановите нужный файл и выполните накат повторно. Например, если случайно было восстановлено слишком много резервных копий журналов и нужная точка остановки восстановления пройдена, нужно перезапустить последовательность.  
  
 Последовательность восстановления может быть прервана и перезапущена при восстановлении всего содержимого соответствующих файлов.  
  
## <a name="reverting-a-database-to-a-database-snapshot"></a>Восстановление базы данных к моментальному снимку базы данных  
 Объект *операция восстановления базы данных* (указанный с помощью параметра DATABASE_SNAPSHOT) принимает полный исходной базы данных назад во времени, восстанавливая ее времени моментального снимка базы данных, т.е. перезаписывая базы данных-источника с данными из точки в время сохраняется в указанной базе данных моментального снимка. В данный момент может существовать только моментальный снимок, к которому выполняется восстановление. Затем операция отката вновь создает журнал (поэтому впоследствии нельзя будет выполнить накат возвращенной базы данных к точке пользовательской ошибки).  
  
 Потеря данных затронет только изменения в базе данных, произведенные после создания моментального снимка. Метаданные возвращенной базы данных соответствуют метаданным времени создания моментального снимка. Однако при возвращении к моментальному снимку удаляются все полнотекстовые каталоги.  
  
 Возврат из моментальных снимков базы данных не предназначен для восстановления носителей. В отличие от обычного резервного набора данных, моментальный снимок базы данных является неполной копией файлов базы данных. В том случае, если база данных или моментальный снимок базы данных повреждены, возврат из моментального снимка может оказаться невозможным. Более того, даже если оно окажется возможным, восстановление в случае повреждения вряд ли поможет устранить проблему.  
  
### <a name="restrictions-on-reverting"></a>Ограничения на возврат  
 Возврат не поддерживается в следующих условиях.  
  
-   Если база данных-источник содержит файловые группы, доступные только для чтения, или сжатые файловые группы.  
  
-   Если какие-либо файлы, работавшие в режиме «вне сети» во время создания моментального снимка, сейчас работают автономно.  
  
-   Если в настоящий момент существует несколько моментальных снимков базы данных.  
  
 Дополнительные сведения см. в разделе [восстановление моментального снимка базы данных](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md).  
  
## <a name="security"></a>безопасность  
 В операции создания резервной копии могут дополнительно указываться пароли для набора носителей, резервного набора данных или и того и другого. Если для набора носителей или резервного набора данных установлен пароль, то в инструкции RESTORE необходимо указывать правильные пароли. Эти пароли предотвращают несанкционированные операции восстановления и присоединения резервных наборов данных к носителю при помощи инструментальных средств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако защищенный паролем носитель может быть переписан инструкцией BACKUP с параметром FORMAT.  
  
> [!IMPORTANT]  
>  Данный пароль не обеспечивает надежную защиту. Он предназначен для предотвращения неверного восстановления при использовании средств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] авторизованными или неавторизованными пользователями. При этом остается возможным чтение данных резервных копий с помощью других средств или замена пароля. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Защита резервных копий, рекомендуется хранить ленты резервной копии в безопасном месте или создать резервную копию файлов, которые защищены списками управления доступом (ACL). Списки ACL должны располагаться в корневом каталоге, в котором создаются резервные копии.  
>   
>  Сведения о резервном копировании SQL Server и восстановление с помощью хранилища больших двоичных объектов Windows Azure см. в разделе [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
### <a name="permissions"></a>Permissions  
 Если восстанавливаемая база данных не существуют, для выполнения инструкции RESTORE у пользователя должны быть разрешения CREATE DATABASE. Если база данных существует, разрешения на выполнение инструкции RESTORE по умолчанию предоставлены членам предопределенных ролей сервера **sysadmin** и **dbcreator** , а также владельцу базы данных (**dbo**) (для параметра FROM DATABASE_SNAPSHOT база данных всегда существует).  
  
 Разрешения на выполнение инструкции RESTORE даются ролям, в которых данные о членстве всегда доступны серверу. Так как членство в предопределенной роли базы данных может быть проверено только тогда, когда база данных доступна и не повреждена, что не всегда имеет место при выполнении инструкции RESTORE, члены предопределенной роли базы данных **db_owner** не имеют разрешений RESTORE.  
  
##  <a name="examples"></a> Примеры  
 Во всех примерах предполагается, что выполнено полное резервное копирование базы данных.  
  
 Примеры выполнения инструкции RESTORE.  
  
-   A. [Восстановление всей базы данных](#restoring_full_db)  
  
-   Б. [Восстановление полной и разностной резервной копии](#restoring_full_n_differential_db_backups)  
  
-   В. [Восстановление базы данных с использованием синтаксиса RESTART](#restoring_db_using_RESTART)  
  
-   Г. [Восстановление базы данных и перемещение файлов](#restoring_db_n_move_files)  
  
-   Д. [Копирование базы данных с помощью резервного КОПИРОВАНИЯ и восстановления](#copying_db_using_bnr)  
  
-   Е. [Восстановление состояния на определенный момент времени с помощью STOPAT](#restoring_to_pit_using_STOPAT)  
  
-   Ж. [Восстановление журнала транзакций до метки](#restoring_transaction_log_to_mark)  
  
-   З. [Восстановление с использованием синтаксиса TAPE](#restoring_using_TAPE)  
  
-   И. [Восстановление с использованием синтаксиса FILE и FILEGROUP](#restoring_using_FILE_n_FG)  
  
-   К. [Возврат из моментального снимка базы данных](#reverting_from_db_snapshot)  
  
-   Л. [Восстановление из службы хранилища больших двоичных объектов Microsoft Azure](#Azure_Blob)  
  
> **Примечание:** Дополнительные примеры см. подразделы по восстановлению, перечисленных в [восстановления и восстановления Обзор &#40; SQL Server &#41; ](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md).  
  
###  <a name="restoring_full_db"></a> A. Восстановление всей базы данных  
 В следующем примере производится восстановление базы данных из полной резервной копии, находящейся на логическом устройстве резервного копирования на магнитной ленте `AdventureWorksBackups`. Пример создания этого устройства см. в разделе [устройства резервного копирования](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
```  
RESTORE DATABASE AdventureWorks2012   
   FROM AdventureWorks2012Backups;  
```  
  
> **Примечание:** для базы данных, использующих модель восстановления с неполным протоколированием или полной, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуется в большинстве случаев, резервное копирование заключительного фрагмента журнала перед восстановлением базы данных. Дополнительные сведения см. в статье [Резервные копии заключительного фрагмента журнала (SQL Server)](../../relational-databases/backup-restore/tail-log-backups-sql-server.md).  
  
 [&#91; Начало примеры &#93;](#examples)  
  
###  <a name="restoring_full_n_differential_db_backups"></a> Б. Восстановление полной и разностной резервных копий базы данных  
 В данном примере производится восстановление полной резервной копии базы данных, за которым следует восстановление из разностной резервной копии с устройства резервного копирования `Z:\SQLServerBackups\AdventureWorks2012.bak`, на котором содержатся обе резервные копии. Полная резервная копия базы данных — это шестой резервный набор данных на устройстве (`FILE = 6`), а разностная резервная копия базы данных — девятый резервный набор данных на устройстве (`FILE = 9`). База данных будет восстановлена после восстановления разностной резервной копии.  
  
```  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'  
   WITH FILE = 6  
      NORECOVERY;  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'  
   WITH FILE = 9  
      RECOVERY;  
```  
  
 [&#91; Начало примеры &#93;](#examples)  
  
###  <a name="restoring_db_using_RESTART"></a> В. Восстановление базы данных с использованием синтаксиса RESTART  
 В данном примере параметр `RESTART` используется для перезапуска операции `RESTORE`, прерванной ошибкой питания на сервере.  
  
```  
-- This database RESTORE halted prematurely due to power failure.  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorksBackups;  
-- Here is the RESTORE RESTART operation.  
RESTORE DATABASE AdventureWorks2012   
   FROM AdventureWorksBackups WITH RESTART;  
```  
  
 [&#91; Начало примеры &#93;](#examples)  
  
###  <a name="restoring_db_n_move_files"></a> Г. Восстановление базы данных и перемещение файлов  
 В следующем примере производится полное восстановление базы данных и журнала транзакций, после чего восстановленная база данных перемещается в каталог `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data`.  
  
```  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorksBackups  
   WITH NORECOVERY,   
      MOVE 'AdventureWorks2012_Data' TO   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\NewAdvWorks.mdf',   
      MOVE 'AdventureWorks2012_Log'   
TO 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\NewAdvWorks.ldf';  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorksBackups  
   WITH RECOVERY;  
```  
  
 [&#91; Начало примеры &#93;](#examples)  
  
###  <a name="copying_db_using_bnr"></a> Д. Копирование базы данных с помощью BACKUP и RESTORE  
 В следующем примере с помощью инструкций `BACKUP` и `RESTORE` создается копия базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Инструкция `MOVE` восстанавливает файлы данных и журнала в указанные места. Количество и имена восстанавливаемых файлов базы данных можно определить с помощью инструкции `RESTORE FILELISTONLY`. Новая копия базы данных называется `TestDB`. Дополнительные сведения см. в разделе [Инструкция RESTORE FILELISTONLY (Transact-SQL)](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md).  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO AdventureWorksBackups ;  
  
RESTORE FILELISTONLY   
   FROM AdventureWorksBackups ;  
  
RESTORE DATABASE TestDB   
   FROM AdventureWorksBackups   
   WITH MOVE 'AdventureWorks2012_Data' TO 'C:\MySQLServer\testdb.mdf',  
   MOVE 'AdventureWorks2012_Log' TO 'C:\MySQLServer\testdb.ldf';  
GO  
```  
  
 [&#91; Начало примеры &#93;](#examples)  
  
###  <a name="restoring_to_pit_using_STOPAT"></a> Е. Восстановление состояния на определенный момент времени с помощью STOPAT  
 В следующем примере база данных восстанавливается в состояние на `12:00 AM``April 15, 2020` и демонстрируется операция восстановления, использующая несколько резервных копий журналов. На устройстве резервного копирования `AdventureWorksBackups`полная резервная копия базы данных, подлежащей восстановлению, — это третий резервный набор данных на устройстве (`FILE = 3`), резервная копия первого журнала — это четвертый резервный набор (`FILE = 4`), резервная копия второго журнала — это пятый резервный набор (`FILE = 5`).  
  
```  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorksBackups  
   WITH FILE=3, NORECOVERY;  
  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorksBackups  
   WITH FILE=4, NORECOVERY, STOPAT = 'Apr 15, 2020 12:00 AM';  
  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorksBackups  
   WITH FILE=5, NORECOVERY, STOPAT = 'Apr 15, 2020 12:00 AM';  
RESTORE DATABASE AdventureWorks2012 WITH RECOVERY;  
  
```  
  
 [&#91; Начало примеры &#93;](#examples)  
  
###  <a name="restoring_transaction_log_to_mark"></a>Ж. Восстановление журнала транзакций до метки  
 В следующем примере журнал транзакций восстанавливается до метки в помеченной транзакции с именем `ListPriceUpdate`.  
  
```  
USE AdventureWorks2012  
GO  
BEGIN TRANSACTION ListPriceUpdate  
   WITH MARK 'UPDATE Product list prices';  
GO  
  
UPDATE Production.Product  
   SET ListPrice = ListPrice * 1.10  
   WHERE ProductNumber LIKE 'BK-%';  
GO  
  
COMMIT TRANSACTION ListPriceUpdate;  
GO  
  
-- Time passes. Regular database   
-- and log backups are taken.  
-- An error occurs in the database.  
USE master;  
GO  
  
RESTORE DATABASE AdventureWorks2012  
FROM AdventureWorksBackups  
WITH FILE = 3, NORECOVERY;  
GO  
  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorksBackups   
   WITH FILE = 4,  
   RECOVERY,   
   STOPATMARK = 'UPDATE Product list prices';  
```  
  
 [&#91; Начало примеры &#93;](#examples)  
  
###  <a name="restoring_using_TAPE"></a>З. Восстановление с использованием синтаксиса TAPE  
 В следующем примере производится восстановление базы данных из полной резервной копии, находящейся на устройстве резервного копирования `TAPE`.  
  
```  
RESTORE DATABASE AdventureWorks2012   
   FROM TAPE = '\\.\tape0';  
```  
  
 [&#91; Начало примеры &#93;](#examples)  
  
###  <a name="restoring_using_FILE_n_FG"></a>Я. Восстановление с использованием синтаксиса FILE и FILEGROUP  
 В следующем примере производится восстановление базы данных `MyDatabase`, содержащей два файла, одну вторичную файловую группу и один журнал транзакций. Эта база данных использует модель полного восстановления.  
  
 Резервная копия базы данных представляет собой девятый резервный набор данных в наборе носителей на логическом устройстве резервного копирования с именем `MyDatabaseBackups`. Затем производится восстановление трех резервных копий журнала из следующих трех резервных наборов данных (`10`, `11` и `12`) на устройстве `MyDatabaseBackups` с помощью предложения `WITH NORECOVERY`. База данных будет восстановлена после восстановления последней резервной копии журналов.  
  
> **Примечание:** восстановление выполняется как отдельный шаг с целью снижения возможности преждевременного восстановления, перед всеми журнала были восстановлены резервные копии.  
  
 Обратите внимание на два типа параметров `RESTORE DATABASE` в инструкции `FILE`. Параметры `FILE`, предшествующие имени устройства резервного копирования, указывают логические имена файлов базы данных, которые будут восстановлены из резервного набора данных, например `FILE = 'MyDatabase_data_1'`. Этот резервный набор данных не является первой резервной копией базы данных в наборе носителей, поэтому его позиция указывается параметром `FILE` в предложении `WITH`: `FILE=9`.  
  
```  
RESTORE DATABASE MyDatabase  
   FILE = 'MyDatabase_data_1',  
   FILE = 'MyDatabase_data_2',  
   FILEGROUP = 'new_customers'  
   FROM MyDatabaseBackups  
   WITH   
      FILE = 9,  
      NORECOVERY;  
GO  
-- Restore the log backups.  
RESTORE LOG MyDatabase  
   FROM MyDatabaseBackups  
   WITH FILE = 10,   
      NORECOVERY;  
GO  
RESTORE LOG MyDatabase  
   FROM MyDatabaseBackups  
   WITH FILE = 11,   
      NORECOVERY;  
GO  
RESTORE LOG MyDatabase  
   FROM MyDatabaseBackups  
   WITH FILE = 12,   
      NORECOVERY;  
GO  
--Recover the database:  
RESTORE DATABASE MyDatabase WITH RECOVERY;  
GO  
```  
  
 [&#91; Начало примеры &#93;](#examples)  
  
###  <a name="reverting_from_db_snapshot"></a>ДЖ. Возврат из моментального снимка базы данных  
 В следующем примере производится восстановление базы данных к моментальному снимку базы данных. В этом примере предполагается, что в базе данных в настоящее время существует только один моментальный снимок. Пример создания этого моментального снимка базы данных см. в разделе [создать моментальный снимок базы данных &#40; Transact-SQL &#41; ](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md).  
  
> **Примечание:** возврат к моментальному снимку удаляются все полнотекстовые каталоги.  
  
```  
USE master;    
RESTORE DATABASE AdventureWorks2012 FROM DATABASE_SNAPSHOT = 'AdventureWorks_dbss1800';  
GO  
```  
 Дополнительные сведения см. в разделе [восстановление моментального снимка базы данных](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md).  

 [&#91; Начало примеры &#93;](#examples)  
  
###  <a name="Azure_Blob"></a>Л. Восстановление из службы хранилища больших двоичных объектов Microsoft Azure  
В следующих трех примера осуществляется с помощью службы хранилища Microsoft Azure.  Имя учетной записи хранилища — `mystorageaccount`.  Контейнер для файлов данных называется `myfirstcontainer`.  Контейнер для файлов резервных копий называется `mysecondcontainer`.  Политика доступа была создана с правами на чтение, запись, delete и список, для каждого контейнера.  Учетные данные SQL Server были созданы с помощью подписанные URL-адреса, которые связаны с хранимой политики доступа.  Сведения о резервном копировании SQL Server и восстановление с помощью хранилища больших двоичных объектов Microsoft Azure см. в разделе [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  

**K1.  Восстановление полной резервной копии с помощью службы хранилища Microsoft Azure**  
Полной резервной копии, расположенной на `mysecondcontainer`, из `Sales` будет восстановлен в `myfirstcontainer`.  `Sales`не существует в настоящее время на сервере. 
```
RESTORE DATABASE Sales
  FROM URL = 'https://mystorageaccount.blob.core.windows.net/mysecondcontainer/Sales.bak'   
  WITH  MOVE 'Sales_Data1' to 'https://mystorageaccount.blob.core.windows.net/myfirstcontainer/Sales_Data1.mdf', 
  MOVE 'Sales_log' to 'https://mystorageaccount.blob.core.windows.net/myfirstcontainer/Sales_log.ldf', 
  STATS = 10;
```

**K2. Восстановление полной резервной копии с помощью службы хранилища Microsoft Azure в локальное хранилище**  
Полной резервной копии, расположенной на `mysecondcontainer`, из `Sales` будут восстановлены в локальное хранилище.  `Sales`не существует в настоящее время на сервере.
```
RESTORE DATABASE Sales
  FROM URL = 'https://mystorageaccount.blob.core.windows.net/mysecondcontainer/Sales.bak'   
  WITH  MOVE 'Sales_Data1' to 'H:\DATA\Sales_Data1.mdf', 
  MOVE 'Sales_log' to 'O:\LOG\Sales_log.ldf', 
  STATS = 10;
```
  
**K3. Восстановление полной резервной копии из локального хранилища для службы хранилища Microsoft Azure**  
```
RESTORE DATABASE Sales
  FROM DISK = 'E:\BAK\Sales.bak'
  WITH  MOVE 'Sales_Data1' to 'https://mystorageaccount.blob.core.windows.net/myfirstcontainer/Sales_Data1.mdf', 
  MOVE 'Sales_log' to 'https://mystorageaccount.blob.core.windows.net/myfirstcontainer/Sales_log.ldf', 
  STATS = 10;
```  
  

  
 [&#91; Начало примеры &#93;](#examples)  
  
## <a name="much-more-information"></a>Гораздо больше сведений.  
 - [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md) 
- [Резервное копирование и восстановление системных баз данных (SQL Server)](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md) 
 - [Restore a Database Backup Using SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)
 - [Создание резервных копий и восстановление полнотекстовых каталогов и индексов](../../relational-databases/search/back-up-and-restore-full-text-catalogs-and-indexes.md)   
 - [Создание резервных копий реплицируемых баз данных и восстановление из них](../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 - [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 - [Наборы носителей, семейства носителей и резервные наборы данных (SQL Server)](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 - [RESTORE REWINDONLY &#40; Transact-SQL &#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 - [RESTORE VERIFYONLY (Transact-SQL)](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 - [RESTORE FILELISTONLY (Transact-SQL)](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)  
 - [Инструкция RESTORE HEADERONLY (Transact-SQL)](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)  
 - [Журнал и сведения о заголовке резервной копии (SQL Server)](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  

