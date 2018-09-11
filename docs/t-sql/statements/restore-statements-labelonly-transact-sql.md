---
title: RESTORE LABELONLY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/30/2018
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: a522623a06dc2166701dc8f9d67aab41f1bbd2c6
ms.sourcegitcommit: d8e3da95f5a2b7d3997d63c53e722d494b878eec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2018
ms.locfileid: "44171586"
---
# <a name="restore-statements---labelonly-transact-sql"></a>Инструкции RESTORE — LABELONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md )]
  Возвращает результирующий набор, содержащий сведения о носителях резервного копирования, которые определяются данным устройством резервного копирования.  
  
> [!NOTE]  
>  Описания аргументов см. в разделе [Аргументы инструкции RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
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
 Описания аргументов инструкции RESTORE LABELONLY см. в разделе [Аргументы инструкции RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Результирующий набор инструкции RESTORE LABELONLY состоит из единственной строки со следующими сведениями.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**MediaName**|**nvarchar(128)**|Имя носителя.|  
|**MediaSetId**|**uniqueidentifier**|Уникальный идентификационный номер набора носителей.|  
|**FamilyCount**|**int**|Число семейств носителей в наборе носителей.|  
|**FamilySequenceNumber**|**int**|Порядковый номер данного семейства.|  
|**MediaFamilyId**|**uniqueidentifier**|Уникальный идентификационный номер семейства носителей.|  
|**MediaSequenceNumber**|**int**|Порядковый номер конкретного носителя в семействе носителей.|  
|**MediaLabelPresent**|**tinyint**|Содержит ли описание носителя:<br /><br /> **1** = [!INCLUDE[msCoName](../../includes/msconame-md.md)] = Метка носителя Tape Format<br /><br /> **0** = Описание носителя|  
|**MediaDescription**|**nvarchar(255)**|Описание носителя в произвольной текстовой форме или метка носителя Tape Format.|  
|**SoftwareName**|**nvarchar(128)**|Имя программы резервного копирования, записавшей метку.|  
|**SoftwareVendorId**|**int**|Уникальный идентификационный номер поставщика программы, записавшей резервную копию.|  
|**MediaDate**|**datetime**|Дата и время записи метки.|  
|**Mirror_Count**|**int**|Количество зеркал в наборе (1 — 4).<br /><br /> Примечание: метки, записанные для различных зеркал в наборе, идентичны.|  
|**IsCompressed**|**bit**|Указывает, является ли резервная копия сжатой:<br /><br /> 0 = не сжатая;<br /><br /> 1 = сжатая.|  
  
> [!NOTE]  
>  Если для набора носителей определен пароль, инструкция RESTORE LABELONLY возвращает сведения только в том случае, если в аргументе MEDIAPASSWORD задан правильный пароль.  
  
## <a name="general-remarks"></a>Общие замечания  
 Выполнение инструкции RESTORE LABELONLY является быстрым способом узнать, что содержит носитель резервной копии. Поскольку инструкция RESTORE LABELONLY считывает только заголовок носителя, она завершается быстро даже при использовании ленточных устройств большой емкости.  
  
## <a name="security"></a>безопасность  
 Операция резервного копирования может указывать пароль для набора носителей. Если для набора носителей установлен пароль, то в инструкции RESTORE необходимо указать правильный пароль. Пароль предотвращает несанкционированные операции восстановления и присоединения резервных наборов данных к носителю при помощи инструментов [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако пароль не запрещает перезапись носителей с помощью параметра FORMAT инструкции BACKUP.  
  
> [!IMPORTANT]  
>  Данный пароль не обеспечивает надежную защиту. Он предназначен для предотвращения неверного восстановления при использовании средств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] авторизованными или неавторизованными пользователями. При этом остается возможным чтение данных резервных копий с помощью других средств или замена пароля. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Рекомендуемым способом защиты резервных копий является хранение лент с резервными копиями в безопасном месте или создание резервных копий на диске в виде файлов, защищенных соответствующими списками управления доступом (ACL). Списки ACL должны располагаться в корневом каталоге, в котором создаются резервные копии.  
  
### <a name="permissions"></a>Разрешения  
 В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях для получения сведений о резервном наборе данных или устройстве резервного копирования необходимо разрешение CREATE DATABASE. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений для базы данных (Transact-SQL)](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [Наборы носителей, семейства носителей и резервные наборы данных (SQL Server)](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE REWINDONLY (Transact-SQL)](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE VERIFYONLY (Transact-SQL)](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Журнал и сведения о заголовке резервной копии (SQL Server)](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  
