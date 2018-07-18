---
title: Представления информационной схемы системы (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- information schema views
- schemas [SQL Server], information schema views
- metadata [SQL Server], views
- views [SQL Server], information schema
- system views [SQL Server], information schema
ms.assetid: 7e9f1dfe-27e9-40e7-8fc7-bfc5cae6be10
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2a3c0ef6d8a3c4c774b441e807c4ca513b214f26
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33240194"
---
# <a name="system-information-schema-views-transact-sql"></a>Представления информационной схемы системы (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Представление информационной схемы является одним из способов получения метаданных, которые предоставляет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Представления информационной схемы обеспечивают внутренний, системный, не зависящий от таблиц обзор метаданных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Представления информационной схемы позволяют приложениям правильно работать, несмотря на значительные изменения, внесенные в базовые системные таблицы. Представления информационной схемы, включенные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], соответствуют стандартному определению ISO для INFORMATION_SCHEMA.  
  
> [!IMPORTANT]  
>  В представления информационной схемы были внесены определенные изменения, нарушающие обратную совместимость. Эти изменения описаны в разделах, посвященных конкретным представлениям.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает соглашения по трехкомпонентному именованию при ссылках на текущий сервер. Стандарт ISO также поддерживает соглашения по трехкомпонентному именованию. Однако имена, которые используются в обоих соглашениях, различаются. Представления информационной схемы определяются в специальной схеме с именем INFORMATION_SCHEMA. Эта схема содержится в любой базе данных. Каждое представление информационной схемы содержит метаданные для всех объектов, хранящихся в этой конкретной базе данных. В следующей таблице представлены связи между именами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и стандартными именами SQL.  
  
|Имя SQL Server|Соответствует эквивалентному стандартному имени SQL|  
|---------------------|-----------------------------------------------|  
|база данных|Каталог|  
|Схема|Схема|  
|Объект|Объект|  
|определяемый пользователем тип данных|Домен|  
  
 Настоящее соглашение по соответствию имен применяется к следующим представлениям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], совместимым со стандартом ISO.  
  
|||  
|-|-|  
|[CHECK_CONSTRAINTS](../../relational-databases/system-information-schema-views/check-constraints-transact-sql.md)|[REFERENTIAL_CONSTRAINTS](../../relational-databases/system-information-schema-views/referential-constraints-transact-sql.md)|  
|[COLUMN_DOMAIN_USAGE](../../relational-databases/system-information-schema-views/column-domain-usage-transact-sql.md)|[ROUTINES](../../relational-databases/system-information-schema-views/routines-transact-sql.md)|  
|[COLUMN_PRIVILEGES](../../relational-databases/system-information-schema-views/column-privileges-transact-sql.md)|[ROUTINE_COLUMNS](../../relational-databases/system-information-schema-views/routine-columns-transact-sql.md)|  
|[COLUMNS](../../relational-databases/system-information-schema-views/columns-transact-sql.md)|[SCHEMATA](../../relational-databases/system-information-schema-views/schemata-transact-sql.md)|  
|[CONSTRAINT_COLUMN_USAGE](../../relational-databases/system-information-schema-views/constraint-column-usage-transact-sql.md)|[TABLE_CONSTRAINTS](../../relational-databases/system-information-schema-views/table-constraints-transact-sql.md)|  
|[CONSTRAINT_TABLE_USAGE](../../relational-databases/system-information-schema-views/constraint-table-usage-transact-sql.md)|[TABLE_PRIVILEGES](../../relational-databases/system-information-schema-views/table-privileges-transact-sql.md)|  
|[DOMAIN_CONSTRAINTS](../../relational-databases/system-information-schema-views/domain-constraints-transact-sql.md)|[TABLES](../../relational-databases/system-information-schema-views/tables-transact-sql.md)|  
|[DOMAINS](../../relational-databases/system-information-schema-views/domains-transact-sql.md)|[VIEW_COLUMN_USAGE](../../relational-databases/system-information-schema-views/view-column-usage-transact-sql.md)|  
|[KEY_COLUMN_USAGE](../../relational-databases/system-information-schema-views/key-column-usage-transact-sql.md)|[VIEW_TABLE_USAGE](../../relational-databases/system-information-schema-views/view-table-usage-transact-sql.md)|  
|[PARAMETERS](../../relational-databases/system-information-schema-views/parameters-transact-sql.md)|[VIEWS](../../relational-databases/system-information-schema-views/views-transact-sql.md)|  
  
 Кроме того, некоторые представления содержат ссылки на различные классы данных, например символьные данные или двоичные данные.  
  
 При ссылке на представления информационной схемы необходимо использовать полное имя, включающее имя схемы `INFORMATION_SCHEMA`. Например:  
  
```  
SELECT TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME, COLUMN_DEFAULT  
FROM AdventureWorks2012.INFORMATION_SCHEMA.COLUMNS  
WHERE TABLE_NAME = N'Product';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
