---
title: RESTORE HEADERONLY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/30/2018
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HEADERONLY
- RESTORE HEADERONLY
- RESTORE_HEADERONLY_TSQL
- HEADERONLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup sets [SQL Server], header information
- headers [SQL Server]
- RESTORE HEADERONLY statement
- backup header information [SQL Server]
ms.assetid: 4b88e98c-49c4-4388-ab0e-476cc956977c
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 2facc71bae52bf1e8706abdc6ac874ae16f11575
ms.sourcegitcommit: bfb5e79586fd08d8e48e9df0e9c76d1f6c2004e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "82262103"
---
# <a name="restore-statements---headeronly-transact-sql"></a>Инструкции RESTORE — HEADERONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md )]

  Возвращает результирующий набор, содержащий все данные заголовков резервных копий из всех резервных наборов данных на конкретном устройстве резервного копирования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
 
> [!NOTE]  
>  Описания аргументов см. в разделе [Аргументы инструкции RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
RESTORE HEADERONLY   
FROM <backup_device>   
[ WITH   
 {  
--Backup Set Options  
   FILE = { backup_set_file_number | @backup_set_file_number }   
 | PASSWORD = { password | @password_variable }   
  
--Media Set Options  
 | MEDIANAME = { media_name | @media_name_variable }   
 | MEDIAPASSWORD = { mediapassword | @mediapassword_variable }  
  
--Error Management Options  
 | { CHECKSUM | NO_CHECKSUM }   
 | { STOP_ON_ERROR | CONTINUE_AFTER_ERROR }  
  
--Tape Options  
 | { REWIND | NOREWIND }   
 | { UNLOAD | NOUNLOAD }    
 } [ ,...n ]  
]  
[;]  
  
<backup_device> ::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
   | { DISK | TAPE | URL } = { 'physical_backup_device_name' |  
       @physical_backup_device_name_var }   
}  
  
```  
> [!NOTE] 
> URL-адрес — это формат, который используется для указания расположения и имени файла для хранилища BLOB-объектов Microsoft Azure и поддерживается начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 CU2. Хотя хранилище Microsoft Azure является службой, реализация аналогична дисковому и ленточному хранилищу, чтобы обеспечить единообразное и эффективное восстановление для всех трех устройств.

## <a name="arguments"></a>Аргументы  
 Описания аргументов инструкции RESTORE HEADERONLY см. в разделе [Аргументы инструкции RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Сервер отправляет строку данных заголовка со следующими столбцами для каждой резервной копии на данном устройстве:  
  
> [!NOTE]
>  Инструкция RESTORE HEADERONLY просматривает все резервные наборы данных на носителе. Поэтому для получения этого результирующего набора из ленточных накопителей большой емкости может потребоваться некоторое время. Для быстрого получения сведений о носителе без сбора сведений о каждом резервном наборе данных используйте инструкцию RESTORE LABELONLY или укажите атрибут FILE **=** _номер_файла_резервного_набора_данных_.  
> 
> [!NOTE]
>  Из-за принципов организации формата Tape Format [!INCLUDE[msCoName](../../includes/msconame-md.md)] резервные наборы данных других программ могут занимать место на том же носителе, на котором располагаются резервные наборы данных [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В результирующий набор команды RESTORE HEADERONLY входят записи для каждого из этих резервных наборов данных.  
  
|Имя столбца|Тип данных|Описание резервных наборов данных SQL Server|  
|-----------------|---------------|--------------------------------------------|  
|**BackupName**|**nvarchar(128)**|Имя резервного набора данных.|  
|**BackupDescription**|**nvarchar(255)**|Описание резервного набора данных.|  
|**BackupType**|**smallint**|Тип резервной копии:<br /><br /> **1** = база данных<br /><br /> **2** = журнал транзакций<br /><br /> **4** = файл<br /><br /> **5** = разностная резервная копия базы данных<br /><br /> **6** = разностная резервная копия файла<br /><br /> **7** = частичная резервная копия<br /><br /> **8** = частичная разностная резервная копия|  
|**ExpirationDate**|**datetime**|Дата истечения срока хранения резервного набора данных.|  
|**Compressed**|**BIT(1)**|Сжат ли резервный набор данных с помощью программных методов сжатия:<br /><br /> **0** = Нет<br /><br /> **1** = Да|  
|**Положение**|**smallint**|Позиция резервного набора данных в томе (для использования с параметром FILE =).|  
|**DeviceType**|**tinyint**|Число, соответствующее устройству, используемому для операции резервного копирования.<br /><br /> Диск:<br /><br /> **2** = логическое<br /><br /> **102** = физическое<br /><br /> Лента:<br /><br /> **5** = логическое<br /><br /> **105** = физическое<br /><br /> Виртуальное устройство:<br /><br /> **7** = логическое<br /><br /> **107** = физическое<br /><br /> Имена логических устройств и их номера находятся в таблице **sys.backup_devices**. Дополнительные сведения см. в разделе [sys.backup_devices (Transact-SQL)](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md).|  
|**UserName**|**nvarchar(128)**|Имя пользователя, выполнившего операцию резервного копирования.|  
|**ServerName**|**nvarchar(128)**|Имя сервера, записавшего резервный набор данных.|  
|**DatabaseName**|**nvarchar(128)**|Имя базы данных, для которой была создана резервная копия.|  
|**DatabaseVersion**|**int**|Версия базы данных, для которой была создана резервная копия.|  
|**DatabaseCreationDate**|**datetime**|Дата и время, когда была создана база данных.|  
|**BackupSize**|**numeric(20,0)**|Размер резервной копии, в байтах.|  
|**FirstLSN**|**numeric(25,0)**|Регистрационный номер транзакции из первой записи журнала в резервном наборе данных.|  
|**LastLSN**|**numeric(25,0)**|Регистрационный номер транзакции в журнале для следующей записи журнала после резервного набора данных.|  
|**CheckpointLSN**|**numeric(25,0)**|Регистрационный номер транзакции в журнале для последней контрольной точки на момент создания резервной копии.|  
|**DatabaseBackupLSN**|**numeric(25,0)**|Регистрационный номер транзакции в журнале для последней полной резервной копии базы данных.<br /><br /> **DatabaseBackupLSN** — это "начало контрольной точки", которое активируется при запуске резервного копирования. Этот номер LSN совпадает со значением **FirstLSN**, если резервная копия создается, когда база данных не используется, а репликация не настроена.|  
|**BackupStartDate**|**datetime**|Дата и время начала операции резервного копирования базы данных.|  
|**BackupFinishDate**|**datetime**|Дата и время завершения операции резервного копирования базы данных.|  
|**SortOrder**|**smallint**|Порядок сортировки на сервере. Данный столбец действителен только для резервных копий баз данных. Предоставляется для обратной совместимости.|  
|**CodePage**|**smallint**|Кодовая страница сервера или кодировка, используемый сервером.|  
|**UnicodeLocaleId**|**int**|Параметр конфигурации, определяющий код локали сервера для сортировки символьных данных в Юникоде. Предоставляется для обратной совместимости.|  
|**UnicodeComparisonStyle**|**int**|Параметр конфигурации, определяющий режим сравнения данных в Юникоде на сервере, что обеспечивает дополнительные возможности управления сортировкой. Предоставляется для обратной совместимости.|  
|**CompatibilityLevel**|**tinyint**|Параметр уровня совместимости базы данных, для которой была создана резервная копия.|  
|**SoftwareVendorId**|**int**|Идентификационный номер поставщика программного обеспечения. Для SQL Server это номер **4608** (или **0x1200** в шестнадцатеричном формате).|  
|**SoftwareVersionMajor**|**int**|Основной номер версии сервера, который создал резервный набор данных.|  
|**SoftwareVersionMinor**|**int**|Дополнительный номер версии сервера, который создал резервный набор данных.|  
|**SoftwareVersionBuild**|**int**|Номер построения сервера, который создал резервный набор данных.|  
|**MachineName**|**nvarchar(128)**|Имя компьютера, выполнившего операцию резервного копирования.|  
|**Flags**|**int**|Значения битов отдельных флагов, установленных в **1**:<br /><br /> **1** = резервная копия журналов содержит операции с неполным протоколированием.<br /><br /> **2** = резервная копия моментального снимка.<br /><br /> **4** = во время резервного копирования база данных была доступна только для чтения.<br /><br /> **8** = во время резервного копирования база данных находилась в однопользовательском режиме.<br /><br /> **16** = резервная копия содержит резервные контрольные суммы.<br /><br /> **32** = во время резервного копирования база данных была повреждена, однако операция была продолжена, несмотря на ошибки.<br /><br /> **64** = резервная копия заключительного фрагмента журнала.<br /><br /> **128** = резервная копия заключительного фрагмента журнала с неполными метаданными.<br /><br /> **256** = резервная копия заключительного фрагмента журнала с параметром NORECOVERY.<br /><br /> **Внимание!** Вместо **Flags** рекомендуется использовать индивидуальные столбцы типа Boolean (перечисленные ниже, начиная с **HasBulkLoggedData** и заканчивая **IsCopyOnly**).|  
|**BindingID**|**uniqueidentifier**|Идентификатор привязки для базы данных. Он соответствует **sys.database_recovery_status database_guid**. Новое значение присваивается, когда база данных восстанавливается. Также см. раздел **FamilyGUID** (ниже).|  
|**RecoveryForkID**|**uniqueidentifier**|Идентификатор последней вилки восстановления. Этот столбец соответствует столбцу **last_recovery_fork_guid** в таблице [backupset](../../relational-databases/system-tables/backupset-transact-sql.md).<br /><br /> Для резервных копий данных идентификатор **RecoveryForkID** равен **FirstRecoveryForkID**.|  
|**Параметры сортировки**|**nvarchar(128)**|Параметры сортировки, используемые базой данных.|  
|**FamilyGUID**|**uniqueidentifier**|Идентификатор исходной базы данных, присвоенный в момент ее создания. Это значение остается неизменным при восстановлении базы данных.|  
|**HasBulkLoggedData**|**bit**|**1** = резервная копия журналов содержит операции с неполным протоколированием.|  
|**IsSnapshot**|**bit**|**1** = резервная копия моментального снимка.|  
|**IsReadOnly**|**bit**|**1** = во время резервного копирования база данных была доступна только для чтения.|  
|**IsSingleUser**|**bit**|**1** = во время резервного копирования база данных находилась в однопользовательском режиме.|  
|**HasBackupChecksums**|**bit**|**1** = резервная копия содержит резервные контрольные суммы.|  
|**IsDamaged**|**bit**|**1** = во время резервного копирования база данных была повреждена, однако операция была продолжена, несмотря на ошибки.|  
|**BeginsLogChain**|**bit**|**1** = это первая копия в непрерывной цепочке резервных копий журналов. Цепочка журналов начинается с первой резервной копии журналов, выполненной после создания базы данных либо при переключении с простой модели восстановления на полную модель или на модель восстановления с неполным протоколированием.|  
|**HasIncompleteMetaData**|**bit**|**1** = резервная копия заключительного фрагмента журнала с неполными метаданными.<br /><br /> Дополнительные сведения о резервных копиях заключительных фрагментов журналов с неполными метаданными резервного копирования см. в разделе [Резервные копии заключительного фрагмента журнала (SQL Server)](../../relational-databases/backup-restore/tail-log-backups-sql-server.md).|  
|**IsForceOffline**|**bit**|**1** = резервное копирование выполнено с параметром NORECOVERY; для резервного копирования база данных была переведена в автономный режим.|  
|**IsCopyOnly**|**bit**|**1** = резервная копия только для копирования.<br /><br /> Резервная копия, предназначенная только для копирования, не влияет на обычные процедуры резервного копирования и восстановления базы данных. Дополнительные сведения см. в разделе [Резервные копии только для копирования (SQL Server)](../../relational-databases/backup-restore/copy-only-backups-sql-server.md).|  
|**FirstRecoveryForkID**|**uniqueidentifier**|Идентификатор первой вилки восстановления. Этот столбец соответствует столбцу **first_recovery_fork_guid** в таблице [backupset](../../relational-databases/system-tables/backupset-transact-sql.md).<br /><br /> Для резервных копий данных идентификатор **FirstRecoveryForkID** равен **FirstRecoveryForkID**.|  
|**ForkPointLSN**|**numeric(25,0)** NULL|Если значение **FirstRecoveryForkID** не равно значению **RecoveryForkID**, это регистрационный номер транзакции в журнале для вилки. В противном случае - значение NULL.|  
|**RecoveryModel**|**nvarchar(60)**|Модель восстановления базы данных, одна из:<br /><br /> FULL<br /><br /> BULK-LOGGED;<br /><br /> ПРОСТОЙ|  
|**DifferentialBaseLSN**|**numeric(25,0)** NULL|Для разностной резервной копии с одной основой это значение равно **FirstLSN** базовой копии для разностного копирования. Изменения, у которых номера LSN больше или равны **DifferentialBaseLSN**, включаются в разностную резервную копию.<br /><br /> Для многобазового разностного резервного копирования значение равно NULL, а базовый номер LSN должен быть определен на файловом уровне. Дополнительные сведения см. в разделе [Инструкция RESTORE FILELISTONLY (Transact-SQL)](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md).<br /><br /> Для разностных резервных копий это значение всегда равно NULL.<br /><br /> Дополнительные сведения см. в разделе [Разностные резервные копии (SQL Server)](../../relational-databases/backup-restore/differential-backups-sql-server.md).|  
|**DifferentialBaseGUID**|**uniqueidentifier**|Для разностной резервной копии с одной основой значение является уникальным идентификатором базовой копии для разностного копирования.<br /><br /> Для разностного резервного копирования на основе нескольких базовых копий это значение равно NULL, а базовая копия для разностного копирования должна определяться по отдельным файлам.<br /><br /> Для разностных резервных копий это значение равно NULL.|  
|**BackupTypeDescription**|**nvarchar(60)**|Тип резервной копии, один из:<br /><br /> DATABASE<br /><br /> TRANSACTION LOG (журнал транзакций)<br /><br /> FILE OR FILEGROUP (файл или файловая группа)<br /><br /> DATABASE DIFFERENTIAL (разностная для базы данных)<br /><br /> FILE DIFFERENTIAL PARTIAL (частичная разностная для файла)<br /><br /> PARTIAL DIFFERENTIAL (частичная разностная)|  
|**BackupSetGUID**|**uniqueidentifier** NULL|Уникальный идентификационный номер резервного набора данных, по которому этот набор определяется в носителе.|  
|**CompressedBackupSize**|**bigint**|Число байтов в резервном наборе данных. Для нераспакованных резервных копий это значение совпадает со значением **BackupSize**.<br /><br /> Для вычисления коэффициента сжатия используйте значения **CompressedBackupSize** и **BackupSize**.<br /><br /> Во время обновления базы данных **msdb** это значение устанавливается равным значению столбца **BackupSize**.|  
|**containment**|**tinyint** not NULL|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.<br /><br /> Указывает состояние включения базы данных.<br /><br /> 0 = включение базы данных отключено<br /><br /> 1 = база данных находится в состоянии частичного включения|  
|**KeyAlgorithm**|**nvarchar(32)**|**Применимо к**: с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (накопительное обновление 1) до текущей версии.<br /><br /> Алгоритм шифрования резервной копии. NO_Encryption указывает на то, что резервная копия не зашифрована. Если не удается определить правильное значение, оно должно быть равно NULL.|  
|**EncryptorThumbprint**|**varbinary(20)**|**Применимо к**: с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (накопительное обновление 1) до текущей версии.<br /><br /> Отпечаток шифратора, который будет использоваться для поиска сертификата или асимметричного ключа в базе данных. Если резервная копия не зашифрована, это значение равно NULL.|  
|**EncryptorType**|**nvarchar(32)**|**Применимо к**: с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (накопительное обновление 1) до текущей версии.<br /><br /> Тип используемого шифратора: сертификат или асимметричный ключ. Если резервная копия не зашифрована, это значение равно NULL.|  
  
> [!NOTE]  
>  Если для резервных наборов данных назначены пароли, то инструкция RESTORE HEADERONLY показывает полные сведения только о резервном наборе данных, пароль которого совпадает с указанным в команде для аргумента PASSWORD. Инструкция RESTORE HEADERONLY также показывает полные сведения для незащищенных резервных наборов данных. В столбце **BackupName** для других защищенных паролем резервных наборов данных на носителе будет указано значение " **_Password Protected_** , а все остальные столбцы будут иметь значение NULL.  
  
## <a name="general-remarks"></a>Общие замечания  
 С помощью инструкции RESTORE HEADERONLY клиент может получить все данные из заголовка резервной копии на конкретном устройстве резервного копирования. Для каждой резервной копии на устройстве резервного копирования сервер передает данные заголовка в виде строки.  
  
## <a name="security"></a>Безопасность  
 В операции создания резервной копии могут дополнительно указываться пароли для набора носителей, резервного набора данных или и того и другого. Если для набора носителей или резервного набора данных установлен пароль, то в инструкции RESTORE необходимо указывать правильные пароли. Эти пароли предотвращают несанкционированные операции восстановления и присоединения резервных наборов данных к носителю при помощи инструментов [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако пароль не запрещает перезапись носителей с помощью параметра FORMAT инструкции BACKUP.  
  
> [!IMPORTANT]  
>  Данный пароль не обеспечивает надежную защиту. Он предназначен для предотвращения неверного восстановления при использовании средств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] авторизованными или неавторизованными пользователями. При этом остается возможным чтение данных резервных копий с помощью других средств или замена пароля. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Рекомендуемым способом защиты резервных копий является хранение лент с резервными копиями в безопасном месте или создание резервных копий на диске в виде файлов, защищенных соответствующими списками управления доступом (ACL). Списки ACL должны располагаться в корневом каталоге, в котором создаются резервные копии.  
  
### <a name="permissions"></a>Разрешения  
 Для получения сведений о резервном наборе данных или устройстве резервного копирования требуется разрешение CREATE DATABASE. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений для базы данных (Transact-SQL)](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются данные из заголовка файла на диске `C:\AdventureWorks-FullBackup.bak`.  
  
```  
RESTORE HEADERONLY   
FROM DISK = N'C:\AdventureWorks-FullBackup.bak';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [backupset (Transact-SQL)](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [RESTORE REWINDONLY (Transact-SQL)](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE VERIFYONLY (Transact-SQL)](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Журнал и сведения о заголовке резервной копии (SQL Server)](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)   
 [Включение или отключение вычисления контрольных сумм резервных копий во время резервного копирования или восстановления (SQL Server)](../../relational-databases/backup-restore/enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)   
 [Наборы носителей, семейства носителей и резервные наборы данных (SQL Server)](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [Модели восстановления (SQL Server)](../../relational-databases/backup-restore/recovery-models-sql-server.md)  
  
  
