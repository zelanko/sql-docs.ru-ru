---
title: "MSdatatype_mappings (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSdatatype_mappings
- MSdatatype_mappings_TSQL
dev_langs: TSQL
helpviewer_keywords: MSdatatype_mappings view
ms.assetid: 13cdabb3-6e07-4e8d-ae80-4235022ccc7f
caps.latest.revision: "12"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7ad922397a8c2ed6e0b4faf0f92b84ee8d3408af
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="msdatatypemappings-transact-sql"></a>MSdatatype_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdatatype_mappings** представление сопоставляет типы данных SQL Server в типы данных, используемые в системах управления базами данных SQL Server (СУБД). Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**: dbms_name**|**nvarchar(128)**|— Это имя СУБД. Ниже приведены возможные значения и их описания.<br /><br /> **MSSQLSERVER**: назначением является база данных SQL Server.<br />**ORACLE**: целевой является база данных Oracle.<br />**DB2**: целевой является база данных IBM DB2.<br />**SYBASE**: назначением является база данных Sybase.|  
|**sql_type**|**nvarchar(128)**|— Тип данных SQL Server.|  
|**dest_type**|**nvarchar(128)**|— Имя типа данных SQL Server.|  
|**dest_prec**|**bigint**|Это точность типа данных SQL Server.|  
|**dest_create_params**|**int**|Только для внутреннего применения.|  
|**dest_nullable**|**bit**|Показывает тип данных SQL Server поддерживает значение NULL.|  
  
## <a name="see-also"></a>См. также:  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Указание сопоставления типов данных для издателя Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
