---
title: MSdbms_datatype (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdbms_datatype
- MSdbms_datatype_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_datatype system table
ms.assetid: 606168cc-79a8-442f-ab43-936f8f884d72
author: stevestein
ms.author: sstein
ms.openlocfilehash: 301aa5af9aa34031f381235341f1e7d461675432
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67907514"
---
# <a name="msdbms_datatype-transact-sql"></a>MSdbms_datatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **MSdbms_datatype** содержит полный список собственных типов данных в каждой поддерживаемой системе управления базами данных (СУБД), используемой в качестве издателя или подписчика в гетерогенной репликации базы данных. Эта таблица хранится в базе данных **msdb** .  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**datatype_id**|**int**|Идентифицирует каждый уникальный тип данных.|  
|**dbms_id**|**int**|Идентифицирует СУБД, к которой принадлежит данный тип.|  
|**type**|**имеет sysname**|Имя типа данных (собственное).|  
|**креатепарамс**|**int**|Битовая карта, описывающая сочетание длины, точности и масштаба, применимое к каждому типу данных:<br /><br /> **0x1** = точность.<br /><br /> **0x2** = масштаб.<br /><br /> **0x4** = length.|  
  
## <a name="remarks"></a>Remarks  
 Эта таблица содержит записи для типов данных SQL Server, поскольку экземпляр SQL Server может как подписываться на базу данных, отличную от SQL Server, так и поддерживать публикации для подписчиков, отличных от SQL Server.  
  
## <a name="see-also"></a>См. также:  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Указание сопоставлений типов данных для издателя Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
