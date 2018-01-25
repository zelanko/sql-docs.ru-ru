---
title: "RESTORE FILELISTONLY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RESTORE FILELISTONLY
- RESTORE_FILELISTONLY_TSQL
- FILELISTONLY
- FILELISTONLY_TSQL
dev_langs: TSQL
helpviewer_keywords:
- backups [SQL Server], file lists
- RESTORE FILELISTONLY statement
- listing backed up files
ms.assetid: 0b4b4d11-eb9d-4f3e-9629-6c79cec7a81a
caps.latest.revision: "83"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e6776115033e6e7222abc610673dd8b0aaff81dc
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="restore-statements---filelistonly-transact-sql"></a>Инструкции - RESTORE FILELISTONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает результирующий набор со списком файлов журнала и базы данных, содержащихся в резервном наборе данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Описания аргументов см. в разделе [аргументы инструкции RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RESTORE FILELISTONLY   
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
 Описания аргументов инструкции RESTORE FILELISTONLY см. в разделе [аргументы инструкции RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Клиент может использовать RESTORE FILELISTONLY для получения списка файлов, содержащихся в резервном наборе данных. Эти данные возвращаются как результирующий набор, содержащий одну строку для каждого файла.  
  
|Имя столбца|Тип данных|Описание|  
|-|-|-|  
|LogicalName|**nvarchar(128)**|Логическое имя файла.|  
|PhysicalName|**nvarchar(260)**|Физическое имя или имя файла в операционной системе.|  
|Тип|**char(1)**|Тип файла:<br /><br /> **L** = Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файла журнала<br /><br /> **D**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файла данных<br /><br /> **F** = полнотекстовый каталог<br /><br /> **S** = FileStream, FileTable или [!INCLUDE[hek_2](../../includes/hek-2-md.md)] контейнера|  
|FileGroupName|**nvarchar(128)**|Имя файловой группы, в которую входит файл.|  
|Размер|**numeric(20,0)**|Текущий размер в байтах.|  
|MaxSize|**numeric(20,0)**|Максимальный разрешенный размер в байтах.|  
|FileID|**bigint**|Идентификатор файла, уникальный в пределах базы данных.|  
|CreateLSN|**numeric(25,0)**|Регистрационный номер в журнале, под которым был создан файл.|  
|DropLSN|**numeric(25,0)** значение NULL|Номер LSN, в котором произошло удаление файла. Если файл не удален, установлено значение NULL.|  
|UniqueID|**uniqueidentifier**|Идентификатор GUID файла.|  
|ReadOnlyLSN|**numeric(25,0) значение NULL**|Регистрационный номер в журнале, под которым файловая группа, содержащая файл, изменила тип доступа с «для чтения и записи» на «только для чтения» (самое последнее изменение).|  
|ReadWriteLSN|**numeric(25,0)** значение NULL|Регистрационный номер транзакции в журнале, под которым файловая группа, содержащая файл, изменила тип с «только для чтения» на «для чтения и записи» (самое последнее изменение).|  
|BackupSizeInBytes|**bigint**|Размер резервной копии этого файла в байтах.|  
|SourceBlockSize|**int**|Размер блока физического устройства, содержащего файл, в байтах (не устройства резервного копирования).|  
|FileGroupID|**int**|Идентификатор файловой группы.|  
|LogGroupGUID|**uniqueidentifier NULL**|NULL.|  
|DifferentialBaseLSN|**numeric(25,0)** значение NULL|Для разностных резервных копий изменения номера LSN больше или равно **DifferentialBaseLSN** включаются в разностную резервную копию.<br /><br /> Для других типов резервных копий установлено значение NULL.|  
|DifferentialBaseGUID|**uniqueidentifier**|Для разностных резервных копий — уникальный идентификатор базовой копии для разностного копирования.<br /><br /> Для других типов резервных копий установлено значение NULL.|  
|IsReadOnly|**бит**|**1** = файл доступен только для чтения.|  
|IsPresent|**бит**|**1** = файл присутствует в резервной копии.|  
|TDEThumbprint|**varbinary(32)**|Показывает отпечаток ключа шифрования базы данных. Отпечатком шифратора является хэш SHA-1 сертификата, с которым шифруется ключ. Сведения о шифровании базы данных см. в разделе [прозрачное шифрование данных &#40; Прозрачное шифрование данных &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).|  
|SnapshotURL|**nvarchar(360)**|URL-адрес для файла базы данных, содержащихся в резервном FILE_SNAPSHOT Azure моментального снимка. Возвращает значение NULL, если резервное копирование не FILE_SNAPSHOT.|  
  
## <a name="security"></a>безопасность  
 В операции создания резервной копии могут дополнительно указываться пароли для набора носителей, резервного набора данных или и того и другого. Если для набора носителей или резервного набора данных установлен пароль, то в инструкции RESTORE необходимо указывать правильные пароли. Эти пароли предотвращают несанкционированные операции восстановления и присоединения резервных наборов данных к носителю при помощи [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средства. Однако пароль не запрещает перезапись носителей с помощью параметра FORMAT инструкции BACKUP.  
  
> [!IMPORTANT]  
>  Данный пароль не обеспечивает надежную защиту. Он предназначен для предотвращения неверного восстановления при использовании средств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] авторизованными или неавторизованными пользователями. При этом остается возможным чтение данных резервных копий с помощью других средств или замена пароля. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Рекомендуемым способом защиты резервных копий является хранение лент с резервными копиями в безопасном месте или создание резервных копий на диске в виде файлов, защищенных соответствующими списками управления доступом (ACL). Списки ACL должны располагаться в корневом каталоге, в котором создаются резервные копии.  
  
### <a name="permissions"></a>Разрешения  
 В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях, чтобы получить сведения о резервном наборе данных или устройстве резервного копирования, необходимо разрешение CREATE DATABASE. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений для базы данных (Transact-SQL)](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются данные из устройства резервного копирования с именем `AdventureWorksBackups`. В примере используется параметр `FILE` для указания второго резервного набора данных на устройстве.  
  
```  
RESTORE FILELISTONLY FROM AdventureWorksBackups   
   WITH FILE=2;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [Наборы носителей, семейства носителей и резервные наборы данных (SQL Server)](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE REWINDONLY (Transact-SQL)](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE VERIFYONLY (Transact-SQL)](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Журнал и сведения о заголовке резервной копии (SQL Server)](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  
