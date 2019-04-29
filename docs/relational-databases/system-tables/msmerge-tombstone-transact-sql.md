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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ab57e69118edfe4a647d6baeedf5a10ee8460247
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63026456"
---
# <a name="msmergetombstone-transact-sql"></a>MSmerge_tombstone (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_tombstone** таблица содержит сведения об удаленных строках и позволяет распространять на другие подписчики удаления. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**столбец ROWGUID**|**uniqueidentifier**|Идентификатор строки.|  
|**tablenick**|**int**|Псевдоним таблицы.|  
|**type**|**tinyint**|Тип удаления:<br /><br /> 1 = удаление пользователем.<br /><br /> 5 = строка больше не принадлежит отфильтрованной секции.<br /><br /> 6 = удаление системой.|  
|**журнала обращений и преобразований**|**varbinary(249)**|Указывает версию удаленной записи и ее обновления, известные на момент удаления. Обеспечивает правила согласованного разрешения конфликта, когда подписчик обновляет строку при удалении ее другим подписчиком.|  
|**Создание**|**int**|Назначается при удалении строки. Если подписчик запрашивает поколение N, только захоронения с поколением > = N, отправляются.|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Идентифицирует логическую запись, которой принадлежит удаленная строка.|  
|**logical_record_lineage**|**Varbinary(501)**|Пары псевдонимов подписчиков и номеров версий, используемые для ведения журнала удалений логической записи, которой принадлежит данная строка.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
