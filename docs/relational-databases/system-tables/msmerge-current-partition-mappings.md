---
title: MSmerge_current_partition_mappings | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_current_partition_mappings
- MSmerge_current_partition_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_current_partition_mappings system table
ms.assetid: a3088840-5a30-40f5-8e8a-aa03afc4905f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 993646db8983c0b1737b7fde16e920024c555092
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806762"
---
# <a name="msmergecurrentpartitionmappings"></a>MSmerge_current_partition_mappings
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_current_partition_mappings** таблица хранит по одной строке для каждого идентификатора секции, к которому принадлежит данная измененная строка. Эта таблица хранится в базе данных публикации.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publication_number**|**smallint**|Номер публикации, который хранится в **sysmergepublications**.|  
|**tablenick**|**int**|Псевдоним опубликованной таблицы.|  
|**столбец ROWGUID**|**uniqueidentifier**|Идентификатор данной строки.|  
|**partition_id**|**int**|Идентификатор секции, к которой принадлежит строка. Значение равняется –1, когда изменение строки имеет значение для всех подписчиков.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
