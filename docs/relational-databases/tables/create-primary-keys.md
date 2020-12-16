---
description: Создание первичных ключей
title: Создание первичных ключей | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- primary keys [SQL Server], creating
ms.assetid: 85c623ca-4656-4d70-a9db-ee4d897cd214
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: edc3d1c699000e72dd963fc7b115edb72904329a
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97484506"
---
# <a name="create-primary-keys"></a>Создание первичных ключей


[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

Определить первичный ключ в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Создание первичного ключа автоматически приводит к созданию соответствующего уникального кластеризованного индекса (или некластеризованного при наличии такого указания).

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом

### <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения

- В таблице возможно наличие только одного ограничения по первичному ключу.

- Все столбцы с ограничением PRIMARY KEY должны иметь признак NOT NULL. Если допустимость значения NULL не указана, то для всех столбцов c ограничением PRIMARY KEY устанавливается признак NOT NULL.

### <a name="security"></a><a name="Security"></a> безопасность

#### <a name="permissions"></a><a name="Permissions"></a> Permissions

Создание новой таблицы с первичным ключом требует разрешения CREATE TABLE в базе данных и разрешения ALTER на схему, в которой создается таблица.

Создание первичного ключа в существующей таблице требует разрешения ALTER на таблицу.

## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio

### <a name="to-create-a-primary-key"></a>Создание первичного ключа

1. В обозревателе объектов щелкните правой кнопкой мыши таблицу, в которую необходимо добавить ограничение уникальности, и выберите **Конструктор**.
2. В **Конструкторе таблиц** щелкните селектор строк для столбца базы данных, который необходимо определить в качестве первичного ключа. Чтобы выделить несколько столбцов, нажмите и удерживайте клавишу CTRL и щелкните селекторы строк для остальных столбцов.
3. Щелкните правой кнопкой мыши средство выбора строк столбца и выберите команду **Задать первичный ключ**.

> [!CAUTION]
> Чтобы переопределить первичный ключ, необходимо удалить все связи с существующим первичным ключом и только после этого создавать новый первичный ключ. Появится сообщение, предупреждающее об автоматическом удалении в ходе процесса всех существующих связей.

Ключевой столбец-источник идентифицируется символом первичного ключа в соответствующем селекторе строк.

Если первичный ключ состоит более чем из одного столбца, то в одном столбце могут встречаться дублирующиеся значения, но все сочетания значений изо всех столбцов первичного ключа должны быть уникальными.

При определении составного ключа порядок столбцов в первичном ключе совпадает с порядком столбцов, показанным в таблице. Однако после создания первичного ключа порядок столбцов можно изменить. Дополнительные сведения см. в разделе [Изменение первичных ключей](../../relational-databases/tables/modify-primary-keys.md).

## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL

### <a name="to-create-a-primary-key-in-an-existing-table"></a>Создание первичного ключа в существующей таблице

В следующем примере создается первичный ключ для столбца `TransactionID` в базе данных AdventureWorks.

```sql
ALTER TABLE Production.TransactionHistoryArchive
   ADD CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID);
```

### <a name="to-create-a-primary-key-in-a-new-table"></a>Создание первичного ключа в новой таблице

В следующем примере создается таблица и определяется первичный ключ для столбца `TransactionID` в базе данных AdventureWorks.

```sql
CREATE TABLE Production.TransactionHistoryArchive1
   (
      TransactionID int IDENTITY (1,1) NOT NULL
      , CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID)
   )
;
```

### <a name="to-create-a-primary-key-with-clustered-index-in-a-new-table"></a>Создание первичного ключа с кластеризованным индексом в новой таблице

В следующем примере создается таблица и определяется первичный ключ для столбца `CustomerID` и кластеризованного индекса для `TransactionID` в базе данных AdventureWorks.

```sql
-- Create table to add the clustered index
CREATE TABLE Production.TransactionHistoryArchive1
   (
      CustomerID uniqueidentifier DEFAULT NEWSEQUENTIALID()
      , TransactionID int IDENTITY (1,1) NOT NULL
      , CONSTRAINT PK_TransactionHistoryArchive1_CustomerID PRIMARY KEY NONCLUSTERED (CustomerID)
   )
;

-- Now add the clustered index
CREATE CLUSTERED INDEX CIX_TransactionID ON Production.TransactionHistoryArchive1 (TransactionID);
```

## <a name="see-also"></a>См. также:

- [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)
- [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) 
- [table_constraint](../../t-sql/statements/alter-table-table-constraint-transact-sql.md)
