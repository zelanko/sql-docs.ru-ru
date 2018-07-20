---
title: MSmerge_tombstone (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_tombstone_TSQL
- MSmerge_tombstone
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_tombstone system table
ms.assetid: 8b3fc7bf-729b-40f2-8a26-e7dfbe8ddb38
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: af64c598ccb092a5c0e408496ceba8d97f609124
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102072"
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
|**Создание**|**int**|Назначается при удалении строки. Если подписчик запрашивает поколение N, отправляются только захоронения с поколением >= N.|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Идентифицирует логическую запись, которой принадлежит удаленная строка.|  
|**logical_record_lineage**|**Varbinary(501)**|Пары псевдонимов подписчиков и номеров версий, используемые для ведения журнала удалений логической записи, которой принадлежит данная строка.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
