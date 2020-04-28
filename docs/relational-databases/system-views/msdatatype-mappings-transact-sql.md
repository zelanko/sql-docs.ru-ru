---
title: MSdatatype_mappings (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdatatype_mappings
- MSdatatype_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdatatype_mappings view
ms.assetid: 13cdabb3-6e07-4e8d-ae80-4235022ccc7f
author: stevestein
ms.author: sstein
ms.openlocfilehash: ee1a0cc83b55fc265ae2bb490fd9d5e11fd73f22
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68129624"
---
# <a name="msdatatype_mappings-transact-sql"></a>MSdatatype_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdatatype_mappings** представление сопоставляет типы данных SQL Server с типами данных, используемыми системами управления базами данных (СУБД), отличными от SQL Server. Эта таблица хранится в базе данных **msdb** .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**dbms_name**|**nvarchar(128)**|Имя СУБД. Ниже приведены возможные значения и их описания.<br /><br /> **MSSQLServer**: целевой является SQL Server базой данных.<br />**Oracle**: целевой является база данных Oracle.<br />**DB2**. Назначение — это база данных IBM DB2.<br />**SYBASE**. целевым объектом является база данных Sybase.|  
|**sql_type**|**nvarchar(128)**|Тип данных SQL Server.|  
|**dest_type**|**nvarchar(128)**|Название типа данных, не являющихся данными SQL Server.|  
|**dest_prec**|**bigint**|Точность типа данных, не являющихся данными SQL Server.|  
|**dest_create_params**|**int**|Только для внутреннего применения.|  
|**dest_nullable**|**bit**|Заполняется, если тип данных, не являющихся данными SQL Server, поддерживает значение NULL.|  
  
## <a name="see-also"></a>См. также:  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Указание сопоставлений типов данных для издателя Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
