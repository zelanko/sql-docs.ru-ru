---
title: MSmerge_tombstone (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_tombstone_TSQL
- MSmerge_tombstone
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_tombstone system table
ms.assetid: 8b3fc7bf-729b-40f2-8a26-e7dfbe8ddb38
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4ee4f5a7c48348f819891e298b3a20d5778b2023
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82823430"
---
# <a name="msmerge_tombstone-transact-sql"></a>MSmerge_tombstone (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **MSmerge_tombstone** содержит сведения об удаленных строках и позволяет распространять удаления на другие подписчики. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**rowguid**|**uniqueidentifier**|Идентификатор строки.|  
|**tablenick**|**int**|Псевдоним таблицы.|  
|**type**|**tinyint**|Тип удаления:<br /><br /> 1 = удаление пользователем.<br /><br /> 5 = строка больше не принадлежит отфильтрованной секции.<br /><br /> 6 = удаление системой.|  
|**журнала преобразований**|**varbinary (249)**|Указывает версию удаленной записи и ее обновления, известные на момент удаления. Обеспечивает правила согласованного разрешения конфликта, когда подписчик обновляет строку при удалении ее другим подписчиком.|  
|**поколения**|**int**|Назначается при удалении строки. Если подписчик запрашивает поколение N, отправляются только отметки полного удаления с поколением >= N.|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Идентифицирует логическую запись, которой принадлежит удаленная строка.|  
|**logical_record_lineage**|**Varbinary (501)**|Пары псевдонимов подписчиков и номеров версий, используемые для ведения журнала удалений логической записи, которой принадлежит данная строка.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
