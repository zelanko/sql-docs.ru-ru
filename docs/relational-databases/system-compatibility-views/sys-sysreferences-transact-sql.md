---
title: sys.sysreferences (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sysreferences
- sys.sysreferences_TSQL
- sysreferences
- sysreferences_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysreferences compatibility view
- sysreferences system table
ms.assetid: 81276f13-202e-4e74-962d-46eb98c98d2e
caps.latest.revision: 38
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2198d9eac7eb134703d36df6be9a76d9e9fdf09e
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43061414"
---
# <a name="syssysreferences-transact-sql"></a>sys.sysreferences (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Содержит сопоставления определений FOREIGN KEY со столбцами, являющимися объектами ссылок внутри базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|Идентификатор ограничения FOREIGN KEY.|  
|**fkeyid**|**int**|Идентификатор ссылающейся таблицы.|  
|**rkeyid**|**int**|Идентификатор ссылаемой таблицы.|  
|**rkeyindid**|**smallint**|Индексный идентификатор уникального индекса ссылаемой таблицы, относящийся к ссылаемым ключевым столбцам.|  
|**keycnt**|**smallint**|Количество столбцов в ключе.|  
|**forkeys**|**varbinary(32)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**refkeys**|**varbinary(32)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**fkeydbid**|**smallint**|Зарезервировано.|  
|**rkeydbid**|**smallint**|Зарезервировано.|  
|**fkey1**|**smallint**|Идентификатор ссылочного столбца.|  
|**fkey2**|**smallint**|Идентификатор ссылочного столбца.|  
|**fkey3**|**smallint**|Идентификатор ссылочного столбца.|  
|**fkey4**|**smallint**|Идентификатор ссылочного столбца.|  
|**fkey5**|**smallint**|Идентификатор ссылочного столбца.|  
|**fkey6**|**smallint**|Идентификатор ссылочного столбца.|  
|**fkey7**|**smallint**|Идентификатор ссылочного столбца.|  
|**fkey8**|**smallint**|Идентификатор ссылочного столбца.|  
|**fkey9**|**smallint**|Идентификатор ссылочного столбца.|  
|**fkey10**|**smallint**|Идентификатор ссылочного столбца.|  
|**fkey11**|**smallint**|Идентификатор ссылочного столбца.|  
|**fkey12**|**smallint**|Идентификатор ссылочного столбца.|  
|**fkey13**|**smallint**|Идентификатор ссылочного столбца.|  
|**fkey14**|**smallint**|Идентификатор ссылочного столбца.|  
|**fkey15**|**smallint**|Идентификатор ссылочного столбца.|  
|**fkey16**|**smallint**|Идентификатор ссылочного столбца.|  
|**rkey1**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**rkey2**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**rkey3**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**rkey4**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**rkey5**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**rkey6**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**rkey7**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**rkey8**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**rkey9**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**rkey10**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**rkey11**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**rkey12**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**rkey13**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**rkey14**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**rkey15**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**rkey16**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
