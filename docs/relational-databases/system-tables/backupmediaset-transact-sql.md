---
title: backupmediaset (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- backupmediaset
- backupmediaset_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup media [SQL Server], backupmediaset system table
- backupmediaset system table
ms.assetid: d9c18a93-cab9-4db8-ae09-c6bd8145ab8f
caps.latest.revision: 39
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f394fc3ece4b7eb6c0a5b333ac597effe5c1dcc5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="backupmediaset-transact-sql"></a>backupmediaset (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого резервного набора носителей. Эта таблица хранится в **msdb** базы данных.  
 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**media_set_id**|**int**|Уникальный идентификационный номер набора носителей. Удостоверение, первичный ключ.|  
|**media_uuid**|**uniqueidentifier**|UUID набора носителей. Все [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] наборов носителей имеют UUID.<br /><br /> Для более ранних версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], однако, если набор носителей содержит только одно семейство носителей, **media_uuid** столбец может принимать значение NULL (**media_family_count** -1).|  
|**media_family_count**|**tinyint**|Число семейств носителей в наборе носителей. Может иметь значение NULL.|  
|**name**|**nvarchar(128)**|Имя набора носителей. Может иметь значение NULL.<br /><br /> Дополнительные сведения см. в разделе параметров MEDIANAME и MEDIADESCRIPTION в [резервного КОПИРОВАНИЯ &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md).|  
|**Описание**|**nvarchar(255)**|Текстовое описание набора носителей. Может иметь значение NULL.<br /><br /> Дополнительные сведения см. в разделе параметров MEDIANAME и MEDIADESCRIPTION в [резервного КОПИРОВАНИЯ &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md).|  
|**software_name**|**nvarchar(128)**|Имя программного обеспечения резервного копирования, которое записало метку носителя. Может иметь значение NULL.|  
|**software_vendor_id**|**int**|Идентификационный номер поставщика программного обеспечения, которое записало метку носителя резервной копии. Может иметь значение NULL.<br /><br /> Значение для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является шестнадцатеричным 0x1200.|  
|**MTF_major_version**|**tinyint**|Главный номер версии формата ленты [!INCLUDE[msCoName](../../includes/msconame-md.md)], используемого для формирования этого набора носителей. Может иметь значение NULL.|  
|**mirror_count**|**tinyint**|Число зеркальных отображений в наборе носителей.|  
|**is_password_protected**|**бит**|Защищен ли набор носителей паролем.<br /><br /> 0 = не защищен<br /><br /> 1 = защищен|  
|**is_compressed**|**бит**|Указывает, является ли резервная копия сжатой:<br /><br /> 0 = не сжатая<br /><br /> 1 = сжатая<br /><br /> Во время **msdb** обновления, это значение будет равно NULL. Это означает резервное копирование без сжатия.|  
|**is_encrypted**|**Bit**|Указывает, шифруется ли резервная копия.<br /><br /> 0 = не зашифрована<br /><br /> 1 = зашифрована|  
  
## <a name="remarks"></a>Замечания  
 Инструкция RESTORE VERIFYONLY FROM *устройство_резервного_копирования* WITH LOADHISTORY заполняет столбцы **backupmediaset** таблицу с соответствующими значениями из заголовка набора носителей.  
  
 Чтобы уменьшить число строк в данной таблице, а также в других таблицах резервной копии и журнал, выполните [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) хранимой процедуры.  
  
## <a name="see-also"></a>См. также  
 [Резервное копирование и восстановление таблицы &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile (Transact-SQL)](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup (Transact-SQL)](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediafamily (Transact-SQL)](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [backupset (Transact-SQL)](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Системные таблицы (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
