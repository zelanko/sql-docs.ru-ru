---
title: restorefile (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- restorefile
- restorefile_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restorefile system table
- restoring files [SQL Server], restorefile system table
- file restores [SQL Server], restorefile system table
ms.assetid: 8e40145a-8559-4abe-8e2a-39b818928009
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7414ca1c7d3ef3455aeb3b41c677ebc946a0e3d3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806819"
---
# <a name="restorefile-transact-sql"></a>restorefile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого восстановленного файла, включая файлы, восстановленные косвенно по имени файловой группы. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**restore_history_id**|**int**|Уникальный идентификационный номер, который определяет соответствующую операцию восстановления. Ссылки на **restorehistory(restore_history_id)**.|  
|**file_number**|**numeric(10,0)**|Идентификационный номер восстановленного файла. Этот номер должен быть уникальным в каждой базе данных. Может иметь значение NULL.<br /><br /> Когда база данных возвращается в моментальный снимок базы данных, это значение заполняется так же, как и в случае полного восстановления.|  
|**destination_phys_drive**|**nvarchar(260)**|Диск или секция, где был восстановлен файл. Может иметь значение NULL.<br /><br /> Когда база данных возвращается в моментальный снимок базы данных, это значение заполняется так же, как и в случае полного восстановления.|  
|**destination_phys_name**|**nvarchar(260)**|Имя файла без указания сведений о диске или секции, где был восстановлен файл. Может иметь значение NULL.<br /><br /> Когда база данных возвращается в моментальный снимок базы данных, это значение заполняется так же, как и в случае полного восстановления.|  
  
## <a name="remarks"></a>Примечания  
 Чтобы уменьшить число строк в данной таблице, а также в других резервных и таблицах журнала, выполните [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) хранимой процедуры.  
  
## <a name="see-also"></a>См. также  
 [Резервное копирование и восстановление таблиц &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [restorefilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)   
 [RestoreHistory &#40;Transact-SQL&#41;](../../relational-databases/system-tables/restorehistory-transact-sql.md)   
 [Системные таблицы (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
