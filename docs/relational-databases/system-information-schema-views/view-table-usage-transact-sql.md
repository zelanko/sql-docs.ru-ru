---
description: VIEW_TABLE_USAGE (Transact-SQL)
title: VIEW_TABLE_USAGE (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- VIEW_TABLE_USAGE_TSQL
- VIEW_TABLE_USAGE
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.VIEW_TABLE_USAGE view
- VIEW_TABLE_USAGE view
ms.assetid: 0aeefb3f-02ef-457e-8c42-84ddb26f1c88
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0c4c477efba071a750b476e0ff4a6b96d27b1520
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469870"
---
# <a name="view_table_usage-transact-sql"></a>VIEW_TABLE_USAGE (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Возвращает одну строку для каждой используемой в представлении таблицы в текущей базе данных. Это представление информационной схемы возвращает сведения об объектах, на которые у текущего пользователя есть разрешения.  
  
 Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA.** _view_name_.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**VIEW_CATALOG**|**nvarchar (** 128 **)**|Квалификатор представления.|  
|**VIEW_SCHEMA**|**nvarchar (** 128 **)**|Имя схемы, содержащей представление.<br /><br /> **&#42;&#42; важно &#42;&#42;**  только надежный способ найти схему объекта — запросить представление каталога sys. objects.|  
|**VIEW_NAME**|**sysname**|Имя представления.|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|Квалификатор таблицы.|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|Имя схемы, содержащей базовую таблицу.<br /><br /> **&#42;&#42; важно &#42;&#42;**  только надежный способ найти схему объекта — запросить представление каталога sys. objects.|  
|**TABLE_NAME**|**sysname**|Базовая таблица, на которой базируется представление.|  
  
## <a name="see-also"></a>См. также:  
 [Системные представления &#40;&#41;Transact-SQL ](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40;&#41;Transact-SQL ](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys. sql_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md)   
 [sys. Objects &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.views (Transact-SQL)](../../relational-databases/system-catalog-views/sys-views-transact-sql.md)  
  
  
