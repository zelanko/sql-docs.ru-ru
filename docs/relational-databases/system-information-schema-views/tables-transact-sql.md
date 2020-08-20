---
description: TABLES (Transact-SQL)
title: ТАБЛИЦЫ (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/20/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- TABLES_TSQL
- TABLES
dev_langs:
- TSQL
helpviewer_keywords:
- TABLES view
- INFORMATION_SCHEMA.TABLES view
ms.assetid: 723a9e63-8f6e-4d6e-b570-468cfaf03201
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7401785ff4d87d858f14231531e6546c69d13bf4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469882"
---
# <a name="tables-transact-sql"></a>TABLES (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Возвращает по одной строке для каждой таблицы или представления в текущей базе данных, для которой у текущего пользователя есть разрешения.  
  
 Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA.** _view_name_.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|Квалификатор таблицы.|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|Имя схемы, содержащей таблицу.<br /><br /> Важно только надежный способ найти схему объекта — запросить представление каталога sys. objects. <strong> \* \* \* \* </strong> Представления INFORMATION_SCHEMA могут быть неполными, поскольку они не обновлены для работы со всеми новыми функциями.|  
|**TABLE_NAME**|**sysname**|Имя таблицы или представления.|  
|**TABLE_TYPE**|**varchar (** 10 **)**|Тип таблицы. Может быть VIEW или BASE TABLE.|  
  
## <a name="see-also"></a>См. также:  
 [Системные представления &#40;&#41;Transact-SQL ](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40;&#41;Transact-SQL ](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys. Objects &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)  
  
  
