---
title: Представления схемы системных сведений (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 07/30/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9767c68f80c133a31c5ca33053731a399f1048db
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68670563"
---
# <a name="system-information-schema-views-transact-sql"></a>Представления схемы системных сведений (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Представление информационной схемы является одним из способов получения метаданных, которые предоставляет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Представления информационной схемы обеспечивают внутренний, системный, не зависящий от таблиц обзор метаданных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Представления информационной схемы позволяют приложениям правильно работать, несмотря на значительные изменения, внесенные в базовые системные таблицы. Представления информационной схемы, включенные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], соответствуют стандартному определению ISO для INFORMATION_SCHEMA.

> [!IMPORTANT]
> В представления информационной схемы были внесены определенные изменения, нарушающие обратную совместимость. Эти изменения описаны в разделах, посвященных конкретным представлениям.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает соглашения по трехкомпонентному именованию при ссылках на текущий сервер. Стандарт ISO также поддерживает соглашения по трехкомпонентному именованию. Однако имена, которые используются в обоих соглашениях, различаются. Представления информационной схемы определяются в специальной схеме с именем INFORMATION_SCHEMA. Эта схема содержится в любой базе данных. Каждое представление информационной схемы содержит метаданные для всех объектов, хранящихся в этой конкретной базе данных. В следующей таблице представлены связи между именами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и стандартными именами SQL.

|Имя SQL Server|Соответствует эквивалентному стандартному имени SQL|
|---------------------|-----------------------------------------------|
|База данных|Каталог|
|схема|схема|
|Объект|Объект|
|определяемый пользователем тип данных|Домен|

Настоящее соглашение по соответствию имен применяется к следующим представлениям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], совместимым со стандартом ISO.

|||
|-|-|
|[CHECK_CONSTRAINTS](../../relational-databases/system-information-schema-views/check-constraints-transact-sql.md)|[REFERENTIAL_CONSTRAINTS](../../relational-databases/system-information-schema-views/referential-constraints-transact-sql.md)|
|[COLUMN_DOMAIN_USAGE](../../relational-databases/system-information-schema-views/column-domain-usage-transact-sql.md)|[ROUTINES](../../relational-databases/system-information-schema-views/routines-transact-sql.md)|
|[COLUMN_PRIVILEGES](../../relational-databases/system-information-schema-views/column-privileges-transact-sql.md)|[ROUTINE_COLUMNS](../../relational-databases/system-information-schema-views/routine-columns-transact-sql.md)|
|[СТОЛБЦЕ](../../relational-databases/system-information-schema-views/columns-transact-sql.md)|[SCHEMATA](../../relational-databases/system-information-schema-views/schemata-transact-sql.md)|
|[CONSTRAINT_COLUMN_USAGE](../../relational-databases/system-information-schema-views/constraint-column-usage-transact-sql.md)|[TABLE_CONSTRAINTS](../../relational-databases/system-information-schema-views/table-constraints-transact-sql.md)|
|[CONSTRAINT_TABLE_USAGE](../../relational-databases/system-information-schema-views/constraint-table-usage-transact-sql.md)|[TABLE_PRIVILEGES](../../relational-databases/system-information-schema-views/table-privileges-transact-sql.md)|
|[DOMAIN_CONSTRAINTS](../../relational-databases/system-information-schema-views/domain-constraints-transact-sql.md)|[ТАБЛИЦЕ](../../relational-databases/system-information-schema-views/tables-transact-sql.md)|
|[ДОМЕНЫ](../../relational-databases/system-information-schema-views/domains-transact-sql.md)|[VIEW_COLUMN_USAGE](../../relational-databases/system-information-schema-views/view-column-usage-transact-sql.md)|
|[KEY_COLUMN_USAGE](../../relational-databases/system-information-schema-views/key-column-usage-transact-sql.md)|[VIEW_TABLE_USAGE](../../relational-databases/system-information-schema-views/view-table-usage-transact-sql.md)|
|[ПАРАМЕТРЫ](../../relational-databases/system-information-schema-views/parameters-transact-sql.md)|[Представления](../../relational-databases/system-information-schema-views/views-transact-sql.md)|

Кроме того, некоторые представления содержат ссылки на различные классы данных, например символьные данные или двоичные данные.

При ссылке на представления информационной схемы необходимо использовать полное имя, включающее имя схемы `INFORMATION_SCHEMA`. Пример:

```sql
SELECT TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME, COLUMN_DEFAULT
FROM AdventureWorks2012.INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME = N'Product';
```

## <a name="see-also"></a>См. также:

- [Системные представления &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)
- [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)
- [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md) 
