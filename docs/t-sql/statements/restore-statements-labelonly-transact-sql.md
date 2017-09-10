---
title: "RESTORE LABELONLY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LABELONLY
- RESTORE_LABELONLY_TSQL
- LABELONLY_TSQL
- RESTORE LABELONLY
dev_langs:
- TSQL
helpviewer_keywords:
- RESTORE LABELONLY statement
- backup media [SQL Server], content information
ms.assetid: 7cf0641e-0d55-4ffb-9500-ecd6ede85ae5
caps.latest.revision: 46
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f69efb096931108fdaea084b337fcb319f7cfb6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="restore-statements---labelonly-transact-sql"></a>Инструкции - RESTORE LABELONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает результирующий набор, содержащий сведения о носителях резервного копирования, которые определяются данным устройством резервного копирования.  
  
> [!NOTE]  
>  Описания аргументов см. в разделе [аргументы инструкции RESTORE & #40; Transact-SQL & #41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RESTORE LABELONLY   
FROM <backup_device>   
[ WITH   
 {  
--Media Set Options  
   MEDIANAME = { media_name | @media_name_variable }   
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
 Описания аргументов инструкции RESTORE LABELONLY см. в разделе [аргументы инструкции RESTORE & #40; Transact-SQL & #41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Результирующий набор инструкции RESTORE LABELONLY состоит из единственной строки со следующими сведениями.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**MediaName**|**nvarchar(128)**|Имя носителя.|  
|**MediaSetId**|**uniqueidentifier**|Уникальный идентификационный номер набора носителей.|  
|**FamilyCount**|**int**|Число семейств носителей в наборе носителей.|  
|**FamilySequenceNumber**|**int**|Порядковый номер данного семейства.|  
|**MediaFamilyId**|**uniqueidentifier**|Уникальный идентификационный номер семейства носителей.|  
|**MediaSequenceNumber**|**int**|Порядковый номер конкретного носителя в семействе носителей.|  
|**MediaLabelPresent**|**tinyint**|Содержит ли описание носителя:<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Метка носителя tape Format<br /><br /> **0** = описание носителя|  
|**MediaDescription**|**nvarchar(255)**|Описание носителя в произвольной текстовой форме или метка носителя Tape Format.|  
|**SoftwareName**|**nvarchar(128)**|Имя программы резервного копирования, записавшей метку.|  
|**SoftwareVendorId**|**int**|Уникальный идентификационный номер поставщика программы, записавшей резервную копию.|  
|**MediaDate**|**datetime**|Дата и время записи метки.|  
|**Mirror_Count**|**int**|Количество зеркал в наборе (1 — 4).<br /><br /> Примечание: Метки, записанные для различных зеркал в наборе являются идентичными.|  
|**IsCompressed**|**bit**|Указывает, является ли резервная копия сжатой:<br /><br /> 0 = не сжатая;<br /><br /> 1 = сжатая.|  
  
> [!NOTE]  
>  Если для набора носителей определен пароль, инструкция RESTORE LABELONLY возвращает сведения только в том случае, если в аргументе MEDIAPASSWORD задан правильный пароль.  
  
## <a name="general-remarks"></a>Общие замечания  
 Выполнение инструкции RESTORE LABELONLY является быстрым способом узнать, что содержит носитель резервной копии. Поскольку инструкция RESTORE LABELONLY считывает только заголовок носителя, она завершается быстро даже при использовании ленточных устройств большой емкости.  
  
## <a name="security"></a>безопасность  
 Операция резервного копирования может указывать пароль для набора носителей. Если для набора носителей установлен пароль, то в инструкции RESTORE необходимо указать правильный пароль. Пароль предотвращает несанкционированные операции восстановления и несанкционированного присоединения резервных наборов данных к носителю при помощи [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средства. Однако пароль не запрещает перезапись носителей с помощью параметра FORMAT инструкции BACKUP.  
  
> [!IMPORTANT]  
>  Данный пароль не обеспечивает надежную защиту. Он предназначен для предотвращения неверного восстановления при использовании средств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] авторизованными или неавторизованными пользователями. При этом остается возможным чтение данных резервных копий с помощью других средств или замена пароля. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Защита резервных копий, рекомендуется хранить ленты резервной копии в безопасном месте или создать резервную копию файлов, которые защищены списками управления доступом (ACL). Списки ACL должны располагаться в корневом каталоге, в котором создаются резервные копии.  
  
### <a name="permissions"></a>Permissions  
 В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях для получения сведений о резервном наборе данных или устройстве резервного копирования необходимо разрешение CREATE DATABASE. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений для базы данных (Transact-SQL)](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [Наборы носителей, семейства носителей и резервные наборы данных (SQL Server)](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE REWINDONLY (Transact-SQL)](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE VERIFYONLY (Transact-SQL)](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Журнал и сведения о заголовке резервной копии (SQL Server)](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  
