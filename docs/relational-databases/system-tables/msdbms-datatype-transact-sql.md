---
title: "MSdbms_datatype (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSdbms_datatype
- MSdbms_datatype_TSQL
dev_langs: TSQL
helpviewer_keywords: MSdbms_datatype system table
ms.assetid: 606168cc-79a8-442f-ab43-936f8f884d72
caps.latest.revision: "24"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dd690436908a61b43b4e7af829e8bc3528fd5305
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="msdbmsdatatype-transact-sql"></a>MSdbms_datatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdbms_datatype** таблица содержит полный список собственных типов данных для каждой поддерживаемой системе управления базами данных (СУБД) использовать в качестве издателя или подписчика в разнородной репликации базы данных. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**datatype_id**|**int**|Идентифицирует каждый уникальный тип данных.|  
|**dbms_id**|**int**|Идентифицирует СУБД, к которой принадлежит данный тип.|  
|**type**|**sysname**|Имя типа данных (собственное).|  
|**CreateParams**|**int**|Битовая карта, описывающая сочетание длины, точности и масштаба, применимое к каждому типу данных:<br /><br /> **0x1** = точность.<br /><br /> **0x2** = масштаб.<br /><br /> **0x4** = длина.|  
  
## <a name="remarks"></a>Замечания  
 Эта таблица содержит записи для типов данных SQL Server, так как экземпляр SQL Server могут подписаться на базе SQL Server и публикации на подписчик, отличных от подписчика SQL Server.  
  
## <a name="see-also"></a>См. также:  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Указание сопоставления типов данных для издателя Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
