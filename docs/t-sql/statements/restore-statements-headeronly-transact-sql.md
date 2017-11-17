---
title: "RESTORE HEADERONLY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/07/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 95
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 694c77c3d59b5565e6c5b25eaf946e9ebaa0e22f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="restore-statements---headeronly-transact-sql"></a>Инструкции - RESTORE HEADERONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает результирующий набор, содержащий все данные заголовков резервных копий из всех резервных наборов данных на конкретном устройстве резервного копирования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Описания аргументов см. в разделе [аргументы инструкции RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
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
   | { DISK | TAPE } = { 'physical_backup_device_name' |  
       @physical_backup_device_name_var }   
}  
  
```  
  
## <a name="arguments"></a>Аргументы  
 Описание аргументов инструкции RESTORE HEADERONLY см. в разделе [аргументы инструкции RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Сервер отправляет строку данных заголовка со следующими столбцами для каждой резервной копии на данном устройстве:  
  
> [!NOTE]  
>  Инструкция RESTORE HEADERONLY просматривает все резервные наборы данных на носителе. Поэтому для получения этого результирующего набора из ленточных накопителей большой емкости может потребоваться некоторое время. Для получения быстрого просмотра носителя без сбора сведений о каждом резервном наборе данных, использовать инструкцию RESTORE LABELONLY или указать ФАЙЛ  **=**  *номер_файла_резервного_набора*.  
  
> [!NOTE]  
>  Из-за особенностей [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tape Format возможна резервные наборы данных из других программ и занимают место на том же носителе [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] резервные наборы данных. В результирующий набор команды RESTORE HEADERONLY входят записи для каждого из этих резервных наборов данных.  
  
|Имя столбца|Тип данных|Описание резервных наборов данных SQL Server|  
|-----------------|---------------|--------------------------------------------|  
|**BackupName**|**nvarchar(128)**|Имя резервного набора данных.|  
|**BackupDescription**|**nvarchar(255)**|Описание резервного набора данных.|  
|**BackupType**|**smallint**|Тип резервной копии:<br /><br /> **1** = база данных<br /><br /> **2** = журнал транзакций<br /><br /> **4** = файл<br /><br /> **5** = разностное копирование базы данных<br /><br /> **6** = разностное копирование файла<br /><br /> **7** = частичная резервная копия<br /><br /> **8** = частичное разностное резервное копирование|  
|**ExpirationDate**|**datetime**|Дата истечения срока хранения резервного набора данных.|  
|**Сжатые**|**BYTE(1)**|Сжат ли резервный набор данных с помощью программных методов сжатия:<br /><br /> **0** = нет<br /><br /> **1** = Да|  
|**Положение**|**smallint**|Позиция резервного набора данных в томе (для использования с параметром FILE =).|  
|**DeviceType**|**tinyint**|Число, соответствующее устройству, используемому для операции резервного копирования.<br /><br /> Диск:<br /><br /> **2** = логическое<br /><br /> **102** = физическое<br /><br /> Лента:<br /><br /> **5** = логическое<br /><br /> **105** = физическое<br /><br /> Виртуальное устройство:<br /><br /> **7** = логическое<br /><br /> **107** = физическое<br /><br /> Имена логических устройств и номера устройств находятся в **sys.backup_devices**; Дополнительные сведения см. в разделе [sys.backup_devices &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md).|  
|**UserName**|**nvarchar(128)**|Имя пользователя, выполнившего операцию резервного копирования.|  
|**ServerName**|**nvarchar(128)**|Имя сервера, записавшего резервный набор данных.|  
|**DatabaseName**|**nvarchar(128)**|Имя базы данных, для которой была создана резервная копия.|  
|**DatabaseVersion**|**int**|Версия базы данных, для которой была создана резервная копия.|  
|**DatabaseCreationDate**|**datetime**|Дата и время, когда была создана база данных.|  
|**BackupSize**|**numeric(20,0)**|Размер резервной копии, в байтах.|  
|**FirstLSN**|**numeric(25,0)**|Регистрационный номер транзакции из первой записи журнала в резервном наборе данных.|  
|**Последний номер LastLSN**|**numeric(25,0)**|Регистрационный номер транзакции в журнале для следующей записи журнала после резервного набора данных.|  
|**CheckpointLSN**|**numeric(25,0)**|Регистрационный номер транзакции в журнале для последней контрольной точки на момент создания резервной копии.|  
|**DatabaseBackupLSN**|**numeric(25,0)**|Регистрационный номер транзакции в журнале для последней полной резервной копии базы данных.<br /><br /> **DatabaseBackupLSN** представляет собой «начало контрольной точки», которая активируется при запуске резервного копирования. Этот номер LSN совпадет с **FirstLSN** Если резервная копия создается, когда база данных бездействует, а репликация не настроена.|  
|**BackupStartDate**|**datetime**|Дата и время начала операции резервного копирования базы данных.|  
|**BackupFinishDate**|**datetime**|Дата и время завершения операции резервного копирования базы данных.|  
|**SortOrder**|**smallint**|Порядок сортировки на сервере. Данный столбец действителен только для резервных копий баз данных. Предоставляется для обратной совместимости.|  
|**CodePage**|**smallint**|Кодовая страница сервера или кодировка, используемый сервером.|  
|**UnicodeLocaleId**|**int**|Параметр конфигурации, определяющий код локали сервера для сортировки символьных данных в Юникоде. Предоставляется для обратной совместимости.|  
|**UnicodeComparisonStyle**|**int**|Параметр конфигурации, определяющий режим сравнения данных в Юникоде на сервере, что обеспечивает дополнительные возможности управления сортировкой. Предоставляется для обратной совместимости.|  
|**Уровень совместимости**|**tinyint**|Параметр уровня совместимости базы данных, для которой была создана резервная копия.|  
|**SoftwareVendorId**|**int**|Идентификационный номер поставщика программного обеспечения. Для SQL Server, это значение является **4608** (или шестнадцатеричное **0x1200**).|  
|**SoftwareVersionMajor**|**int**|Основной номер версии сервера, который создал резервный набор данных.|  
|**SoftwareVersionMinor**|**int**|Дополнительный номер версии сервера, который создал резервный набор данных.|  
|**SoftwareVersionBuild**|**int**|Номер построения сервера, который создал резервный набор данных.|  
|**MachineName**|**nvarchar(128)**|Имя компьютера, выполнившего операцию резервного копирования.|  
|**Флаги**|**int**|Значения битов отдельных флагов Если присвоено **1**:<br /><br /> **1** = журнал резервная копия содержит операции с неполным протоколированием.<br /><br /> **2** = резервное копирование моментальных снимков.<br /><br /> **4** = база данных была доступно только для чтения, во время резервного копирования.<br /><br /> **8** = база данных находилась в однопользовательском режиме во время резервного копирования.<br /><br /> **16** = резервная копия содержит контрольные суммы резервных копий.<br /><br /> **32** = база данных была повреждена во время резервного копирования, но была запрошена операция резервного копирования продолжить несмотря на ошибки.<br /><br /> **64** = резервная копия заключительного фрагмента журнала.<br /><br /> **128** = резервная копия заключительного фрагмента журнала с неполными метаданными.<br /><br /> **256** = резервная копия заключительного фрагмента журнала с параметром NORECOVERY.<br /><br /> **Важно:** рекомендуется вместо **флаги** использовать индивидуальные столбцы типа Boolean (перечисленные ниже, начиная с **HasBulkLoggedData** и заканчивая  **IsCopyOnly**).|  
|**BindingID**|**uniqueidentifier**|Идентификатор привязки для базы данных. Это соответствует **sys.database_recovery_status***database_guid**. Новое значение присваивается, когда база данных восстанавливается. См. также **FamilyGUID** (см. ниже).|  
|**RecoveryForkID**|**uniqueidentifier**|Идентификатор последней вилки восстановления. Этот столбец соответствует столбцу **last_recovery_fork_guid** в [backupset](../../relational-databases/system-tables/backupset-transact-sql.md) таблицы.<br /><br /> Для резервных копий данных **RecoveryForkID** равняется **FirstRecoveryForkID**.|  
|**Параметры сортировки**|**nvarchar(128)**|Параметры сортировки, используемые базой данных.|  
|**FamilyGUID**|**uniqueidentifier**|Идентификатор исходной базы данных, присвоенный в момент ее создания. Это значение остается неизменным при восстановлении базы данных.|  
|**HasBulkLoggedData**|**bit**|**1** = резервная копия журнала, содержащего операции с неполным протоколированием.|  
|**IsSnapshot**|**bit**|**1** = резервное копирование моментальных снимков.|  
|**IsReadOnly**|**bit**|**1** = база данных была доступно только для чтения, во время резервного копирования.|  
|**IsSingleUser**|**bit**|**1** = база данных находилась в однопользовательском режиме во время резервного копирования.|  
|**HasBackupChecksums**|**bit**|**1** = резервная копия содержит контрольные суммы резервных копий.|  
|**IsDamaged**|**bit**|**1** = база данных была повреждена во время резервного копирования, но была запрошена операция резервного копирования продолжить несмотря на ошибки.|  
|**BeginsLogChain**|**bit**|**1** = это первая копия непрерывной цепочки резервных копий журналов. Цепочка журналов начинается с первой резервной копии журналов, выполненной после создания базы данных либо при переключении с простой модели восстановления на полную модель или на модель восстановления с неполным протоколированием.|  
|**Аргумент**|**bit**|**1** = резервная копия заключительного фрагмента журнала с неполными метаданными.<br /><br /> Сведения о резервном копировании заключительного фрагмента журнала с неполными метаданными резервного копирования см. в разделе [резервные копии заключительного фрагмента журнала &#40; SQL Server &#41; ](../../relational-databases/backup-restore/tail-log-backups-sql-server.md).|  
|**IsForceOffline**|**bit**|**1** = резервное копирование выполнено с параметром NORECOVERY; базы данных была переведена в автономный режим резервного копирования.|  
|**IsCopyOnly**|**bit**|**1** = резервная копия только для чтения.<br /><br /> Резервная копия, предназначенная только для копирования, не влияет на обычные процедуры резервного копирования и восстановления базы данных. Дополнительные сведения см. в разделе [Резервные копии только для копирования (SQL Server)](../../relational-databases/backup-restore/copy-only-backups-sql-server.md).|  
|**FirstRecoveryForkID**|**uniqueidentifier**|Идентификатор первой вилки восстановления. Этот столбец соответствует столбцу **first_recovery_fork_guid** в [backupset](../../relational-databases/system-tables/backupset-transact-sql.md) таблицы.<br /><br /> Для резервных копий данных **FirstRecoveryForkID** равняется **RecoveryForkID**.|  
|**ForkPointLSN**|**numeric(25,0)** значение NULL|Если **FirstRecoveryForkID** не равно **RecoveryForkID**, это регистрационный номер вилки. В противном случае - значение NULL.|  
|**RecoveryModel**|**nvarchar(60)**|Модель восстановления базы данных, одна из:<br /><br /> FULL<br /><br /> BULK-LOGGED;<br /><br /> SIMPLE|  
|**DifferentialBaseLSN**|**numeric(25,0)** значение NULL|Для однобазового разностного резервного копирования, это значение равно **FirstLSN** разностного копирования; изменения с номерами LSN больше или равно **DifferentialBaseLSN** включаются в разностную резервную копию.<br /><br /> Для многобазового разностного резервного копирования значение равно NULL, а базовый номер LSN должен быть определен на файловом уровне. Дополнительные сведения см. в разделе [Инструкция RESTORE FILELISTONLY (Transact-SQL)](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md).<br /><br /> Для разностных резервных копий это значение всегда равно NULL.<br /><br /> Дополнительные сведения см. в разделе [Разностные резервные копии (SQL Server)](../../relational-databases/backup-restore/differential-backups-sql-server.md).|  
|**DifferentialBaseGUID**|**uniqueidentifier**|Для разностной резервной копии с одной основой значение является уникальным идентификатором базовой копии для разностного копирования.<br /><br /> Для разностного резервного копирования на основе нескольких базовых копий это значение равно NULL, а базовая копия для разностного копирования должна определяться по отдельным файлам.<br /><br /> Для разностных резервных копий это значение равно NULL.|  
|**BackupTypeDescription**|**nvarchar(60)**|Тип резервной копии, один из:<br /><br /> DATABASE<br /><br /> TRANSACTION LOG (журнал транзакций)<br /><br /> FILE OR FILEGROUP (файл или файловая группа)<br /><br /> DATABASE DIFFERENTIAL (разностная для базы данных)<br /><br /> FILE DIFFERENTIAL PARTIAL (частичная разностная для файла)<br /><br /> PARTIAL DIFFERENTIAL (частичная разностная)|  
|**BackupSetGUID**|**uniqueidentifier** значение NULL|Уникальный идентификационный номер резервного набора данных, по которому этот набор определяется в носителе.|  
|**CompressedBackupSize**|**bigint**|Число байтов в резервном наборе данных. Для распакованных резервных копий это значение совпадает со значением **BackupSize**.<br /><br /> Для вычисления коэффициента сжатия используйте **CompressedBackupSize** и **BackupSize**.<br /><br /> Во время **msdb** обновления, это значение в соответствии со значением из **BackupSize** столбца.|  
|**вложения**|**tinyint** not NULL|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает состояние включения базы данных.<br /><br /> 0 = включение базы данных отключено<br /><br /> 1 = база данных находится в состоянии частичного включения|  
|**KeyAlgorithm**|**nvarchar(32)**|**Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (CU1) до текущей версии.<br /><br /> Алгоритм шифрования резервной копии. NO_Encryption указывает на то, что резервная копия не зашифрована. Если не удается определить правильное значение, оно должно быть равно NULL.|  
|**EncryptorThumbprint**|**varbinary(20)**|**Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (CU1) до текущей версии.<br /><br /> Отпечаток шифратора, который будет использоваться для поиска сертификата или асимметричного ключа в базе данных. Если резервная копия не зашифрована, это значение равно NULL.|  
|**EncryptorType**|**nvarchar(32)**|**Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (CU1) до текущей версии.<br /><br /> Тип используемого шифратора: сертификат или асимметричный ключ. Если резервная копия не зашифрована, это значение равно NULL.|  
  
> [!NOTE]  
>  Если для резервных наборов данных назначены пароли, то инструкция RESTORE HEADERONLY показывает полные сведения только о резервном наборе данных, пароль которого совпадает с указанным в команде для аргумента PASSWORD. Инструкция RESTORE HEADERONLY также показывает полные сведения для незащищенных резервных наборов данных. **BackupName** для других защищенных паролем резервных наборов данных на носителе устанавливается для столбца "*** защищен паролем\*\*\*", и все столбцы имеют значение NULL.  
  
## <a name="general-remarks"></a>Общие замечания  
 С помощью инструкции RESTORE HEADERONLY клиент может получить все данные из заголовка резервной копии на конкретном устройстве резервного копирования. Для каждой резервной копии на устройстве резервного копирования сервер передает данные заголовка в виде строки.  
  
## <a name="security"></a>безопасность  
 В операции создания резервной копии могут дополнительно указываться пароли для набора носителей, резервного набора данных или и того и другого. Если для набора носителей или резервного набора данных установлен пароль, то в инструкции RESTORE необходимо указывать правильные пароли. Эти пароли предотвращают несанкционированные операции восстановления и присоединения резервных наборов данных к носителю при помощи [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средства. Однако пароль не запрещает перезапись носителей с помощью параметра FORMAT инструкции BACKUP.  
  
> [!IMPORTANT]  
>  Данный пароль не обеспечивает надежную защиту. Он предназначен для предотвращения неверного восстановления при использовании средств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] авторизованными или неавторизованными пользователями. При этом остается возможным чтение данных резервных копий с помощью других средств или замена пароля. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Защита резервных копий, рекомендуется хранить ленты резервной копии в безопасном месте или создать резервную копию файлов, которые защищены списками управления доступом (ACL). Списки ACL должны располагаться в корневом каталоге, в котором создаются резервные копии.  
  
### <a name="permissions"></a>Permissions  
 Для получения сведений о резервном наборе данных или устройстве резервного копирования требуется разрешение CREATE DATABASE. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений для базы данных (Transact-SQL)](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются данные из заголовка файла на диске `C:\AdventureWorks-FullBackup.bak`.  
  
```  
RESTORE HEADERONLY   
FROM DISK = N'C:\AdventureWorks-FullBackup.bak'   
WITH NOUNLOAD;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [backupset (Transact-SQL)](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [RESTORE REWINDONLY (Transact-SQL)](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE VERIFYONLY (Transact-SQL)](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Журнал и сведения о заголовке резервной копии (SQL Server)](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)   
 [Включить или отключить контрольные суммы резервных копий во время резервного копирования или восстановления &#40; SQL Server &#41;](../../relational-databases/backup-restore/enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)   
 [Наборы носителей, семейства носителей и резервные наборы данных (SQL Server)](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [Модели восстановления (SQL Server)](../../relational-databases/backup-restore/recovery-models-sql-server.md)  
  
  

