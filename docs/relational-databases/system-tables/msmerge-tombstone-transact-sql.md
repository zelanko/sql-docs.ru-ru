---
description: MSmerge_tombstone (Transact-SQL)
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
ms.openlocfilehash: bf3584d9c4d65bdc498e3eab8edb9b3e0f788fe1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473207"
---
# <a name="msmerge_tombstone-transact-sql"></a>MSmerge_tombstone (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSmerge_tombstone** содержит сведения об удаленных строках и позволяет распространять удаления на другие подписчики. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**уникаль**|**uniqueidentifier**|Идентификатор строки.|  
|**tablenick**|**int**|Псевдоним таблицы.|  
|**type**|**tinyint**|Тип удаления:<br /><br /> 1 = удаление пользователем.<br /><br /> 5 = строка больше не принадлежит отфильтрованной секции.<br /><br /> 6 = удаление системой.|  
|**журнала преобразований**|**varbinary (249)**|Указывает версию удаленной записи и ее обновления, известные на момент удаления. Обеспечивает правила согласованного разрешения конфликта, когда подписчик обновляет строку при удалении ее другим подписчиком.|  
|**поколения**|**int**|Назначается при удалении строки. Если подписчик запрашивает поколение N, отправляются только отметки полного удаления с поколением >= N.|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Идентифицирует логическую запись, которой принадлежит удаленная строка.|  
|**logical_record_lineage**|**Varbinary (501)**|Пары псевдонимов подписчиков и номеров версий, используемые для ведения журнала удалений логической записи, которой принадлежит данная строка.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
