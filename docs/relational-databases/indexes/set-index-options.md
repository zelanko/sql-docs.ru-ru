---
description: Установка параметров индекса
title: Установка параметров индекса | Документация Майкрософт
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: table-view-index, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- ALLOW_ROW_LOCKS option
- SORT_IN_TEMPDB option
- DROP_EXISTING clause
- large data, indexes
- PAD_INDEX
- STATISTICS_NORECOMPUTE
- MAXDOP index option, setting
- index options [SQL Server]
- MAXDOP index option
- IGNORE_DUP_KEY option
- ALLOW_PAGE_LOCKS option
- OPTIMIZE_FOR_SEQUENTIAL_KEY option
- ONLINE
ms.assetid: 7969af33-e94c-41f7-ab89-9d9a2747cd5c
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1803a13e13f75bbb3cf38cbcd841fa7e2dae1508
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97478195"
---
# <a name="set-index-options"></a>Установка параметров индекса

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

В этом разделе описывается процесс изменения свойств индекса в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].

 **В этой статье:**

- **Перед началом работы**

   [Ограничения](#Restrictions)

   [Безопасность](#Security)

- **Изменение свойств индекса различными средствами.**

   [Среда SQL Server Management Studio](#SSMSProcedure)

   [Transact-SQL](#TsqlProcedure)

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом

### <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения

- К индексу с помощью предложения SET в инструкции ALTER INDEX можно немедленно применить следующие параметры: ALLOW_PAGE_LOCKS, ALLOW_ROW_LOCKS, OPTIMIZE_FOR_SEQUENTIAL_KEY, IGNORE_DUP_KEY и STATISTICS_NORECOMPUTE.
- Следующие параметры можно установить при перестройке индекса с помощью инструкции ALTER INDEX REBUILD или CREATE INDEX WITH DROP_EXISTING: PAD_INDEX, FILLFACTOR, SORT_IN_TEMPDB, IGNORE_DUP_KEY, STATISTICS_NORECOMPUTE, ONLINE, ALLOW_ROW_LOCKS, ALLOW_PAGE_LOCKS, MAXDOP и DROP_EXISTING (только CREATE INDEX).

### <a name="security"></a><a name="Security"></a> безопасность

#### <a name="permissions"></a><a name="Permissions"></a> Permissions

Необходимо разрешение ALTER для таблицы или представления.

## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio

### <a name="to-modify-the-properties-of-an-index-in-table-designer"></a>Изменение свойств индекса при помощи конструктора таблиц.

1. В обозревателе объектов щелкните значок плюса, чтобы развернуть базу данных, содержащую таблицу, в которой необходимо изменить свойства индекса.
2. Чтобы развернуть папку **Таблицы** , щелкните значок «плюс».
3. Щелкните правой кнопкой мыши таблицу, в которой необходимо изменить свойства индекса, а затем выберите пункт **Проект**.
4. В меню **Конструктор таблиц** выберите пункт **Индексы и ключи**.
5. Выберите индекс, свойства которого необходимо изменить. Его свойства отобразятся в основной сетке.
6. Измените значения любого или всех свойств, чтобы внести изменения в индекс.
7. Щелкните **Закрыть**.
8. В меню **Файл** выберите пункт **Сохранить**_имя_таблицы_.

### <a name="to-modify-the-properties-of-an-index-in-object-explorer"></a>Изменение свойств индекса при помощи обозревателя объектов.

1. В обозревателе объектов щелкните значок плюса, чтобы развернуть базу данных, содержащую таблицу, в которой необходимо изменить свойства индекса.
2. Чтобы развернуть папку **Таблицы** , щелкните значок «плюс».
3. Щелкните значок плюса (+), чтобы развернуть таблицу, в которой необходимо изменить свойства индекса.
4. Чтобы развернуть папку **Индексы** , щелкните знак «плюс» (+).
5. Щелкните правой кнопкой мыши индекс, свойства которого требуется изменить, и выберите пункт **Свойства**.
6. В разделе **Выбор страницы** щелкните **Параметры**.
7. Измените значения любого или всех свойств, чтобы внести изменения в индекс.
8. Чтобы добавить столбец индекса, удалить или изменить его позицию, выберите страницу **Общие** в диалоговом окне **Свойства индекса ―** _имя_индекса_. Дополнительные сведения см. в разделе [Index Properties F1 Help](../../relational-databases/indexes/index-properties-f1-help.md).

## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL

### <a name="to-see-the-properties-of-all-the-indexes-in-a-table"></a>Просмотр свойств всех индексов в таблице

В следующем примере отображаются свойства всех индексов в таблице базы данных AdventureWorks.

```sql
SELECT i.name AS index_name
   , i.type_desc
   , i.is_unique
   , ds.type_desc AS filegroup_or_partition_scheme
   , ds.name AS filegroup_or_partition_scheme_name
   , i.ignore_dup_key
   , i.is_primary_key
   , i.is_unique_constraint
   , i.fill_factor
   , i.is_padded
   , i.is_disabled
   , i.allow_row_locks
   , i.allow_page_locks
   , i.has_filter
   , i.filter_definition
FROM sys.indexes AS i
   INNER JOIN sys.data_spaces AS ds
      ON i.data_space_id = ds.data_space_id
   WHERE is_hypothetical = 0 AND i.index_id <> 0
       AND i.object_id = OBJECT_ID('HumanResources.Employee')
;
```

#### <a name="to-set-the-properties-of-an-index"></a>Задание свойств индекса

В следующих примерах устанавливаются свойства индексов в базе данных AdventureWorks.

[!code-sql[IndexDDL#AlterIndex4](../../relational-databases/indexes/codesnippet/tsql/set-index-options_1.sql)]

[!code-sql[IndexDDL#AlterIndex2](../../relational-databases/indexes/codesnippet/tsql/set-index-options_2.sql)]

Дополнительные сведения см. в разделе [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md).
