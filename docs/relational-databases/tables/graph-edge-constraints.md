---
title: Ограничения ребер графа | Документация Майкрософт
ms.custom: ''
ms.date: 09/09/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- edge constraints [SQL Server]
- CONNECTION constraints
- edge constraints [Azure SQL Database]
- graph edge constraints
- SQL Graph
author: shkale-msft
ms.author: shkale
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current||=azuresqldb-current'
ms.openlocfilehash: ef0b7952cd589592f6ad6798e4d6f7720b368619
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85633429"
---
# <a name="edge-constraints"></a>Ограничения границ

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/applies-to-version/sql-asdb.md)]

Ограничения ребер могут использоваться для обеспечения целостности данных и применения определенной семантики в таблицах ребер в базе данных графа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="edge-constraints"></a><a name="Connection"></a> Ограничения ребер

В первом выпуске функций графа в таблицах ребер не предусмотрено ничего для конечных точек ребра. То есть ребро в базе данных графа может соединить любой узел с другим, независимо от типа.

В этом выпуске появились ограничения ребер, позволяющие пользователям добавлять ограничения к таблицам ребер, тем самым принудительно применяя определенную семантику и сохраняя целостность данных. При добавлении нового ребра к таблицам ребер с помощью ограничений ребер [!INCLUDE[ssDE](../../includes/ssde-md.md)] обеспечивает существование узлов, которые ребро пытается соединить, в надлежащей таблице узлов. Также гарантируется, что узел не может быть удален, если на него еще ссылается ребро.

### <a name="edge-constraint-clauses"></a>Предложения ограничения ребер

Каждое ограничение ребер состоит из одного или нескольких предложений ограничения ребер. Предложение ограничения ребер — это пара начального и конечного узлов, которые может соединить данное ребро.

Предположим, что в графе есть узлы `Product` и `Customer`, для соединения которых используется ребро `Bought`. Предложение ограничения ребер указывает пару начального и конечного узлов и направление ребра. В этом случае предложение ограничения ребер будет соединять `Customer` с `Product`. То есть вставка ребра `Bought`, идущего от `Customer` к `Product`, будет разрешена. Попытки вставить ребро, которое соединяет `Product` с `Customer`, завершатся ошибкой.

- Предложение ограничения ребра содержит таблицы пар начального и конечного узлов, к которым применяется ограничение ребра.
- Пользователи могут указывать несколько предложений ограничения ребра на одно ограничение, которые будут применяться путем логического сложения.
- Если в одной таблице ребер созданы несколько ограничений, ребра будут разрешены, только если они соответствуют нескольким ограничениям.

### <a name="indexes-on-edge-constraints"></a>Индексы для ограничений ребер

Создание ограничения ребра автоматически не создает соответствующий индекс для столбцов `$from_id` и `$to_id` в таблице ребер. Рекомендуется создать индексы для пары `$from_id` и `$to_id` вручную, если имеются запросы на поиск точек или рабочая нагрузка OLTP.

### <a name="on-delete-referential-actions-on-edge-constraints"></a>Ссылочные действия ON DELETE для ограничений ребер
Каскадные действия для ограничений ребер позволяют пользователям определять действия, которые будет предпринимать ядро СУБД, когда пользователь удаляет узлы, соединяемые указанным ребром. Можно определить следующие ссылочные действия:  
*NO ACTION*   
Ядро СУБД выдает ошибку при попытке удалить узел, соединенный ребрами.  

*CASCADE*   
При удалении узла из базы данных соединяющие его ребра также удаляются.  

## <a name="working-with-edge-constraints"></a>Работа с ограничениями ребер

Ограничение ребра можно задать в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]. Ограничение ребра можно задать только для таблицы ребер графа. Чтобы создать, удалить или изменить ограничение ребра, вам необходимо иметь разрешение **ALTER** для таблицы.

### <a name="create-edge-constraints"></a>Создание ограничений ребер

Следующие примеры демонстрируют создание ограничений ребер в новых или существующих таблицах.

#### <a name="to-create-an-edge-constraint-on-a-new-edge-table"></a>Создание ограничения ребра в новой таблице ребер

В следующем примере создается ограничение ребра в таблице ребер **bought**.

```sql
-- CREATE node and edge tables
CREATE TABLE Customer
   (
      ID INTEGER PRIMARY KEY
      ,CustomerName VARCHAR(100)
   )
AS NODE;
GO
CREATE TABLE Product
   (
      ID INTEGER PRIMARY KEY
      ,ProductName VARCHAR(100)
   )
AS NODE;
GO
CREATE TABLE bought
   (
      PurchaseCount INT
         ,CONSTRAINT EC_BOUGHT CONNECTION (Customer TO Product) ON DELETE NO ACTION
   )
   AS EDGE;
   ```

#### <a name="defining-referential-actions-on-a-new-edge-table"></a>Определение ссылочных действий для новой граничной таблицы 

В следующем примере создается ограничение ребра в граничной таблице **bought** и определяется ссылочное действие ON DELETE CASCADE. 

```sql
-- CREATE node and edge tables
CREATE TABLE Customer
   (
      ID INTEGER PRIMARY KEY
      ,CustomerName VARCHAR(100)
   )
AS NODE;
GO
CREATE TABLE Product
   (
      ID INTEGER PRIMARY KEY
      ,ProductName VARCHAR(100)
   )
AS NODE;
GO
CREATE TABLE bought
   (
      PurchaseCount INT
         ,CONSTRAINT EC_BOUGHT CONNECTION (Customer TO Product) ON DELETE CASCADE
   )
   AS EDGE;
   ```

#### <a name="to-add-edge-constraint-to-an-existing-edge-table"></a>Добавление ограничения ребра в существующую таблицу ребер

В следующем примере используется команда ALTER TABLE для добавления ограничения ребра в таблицу ребер **bought**.

```sql
-- CREATE node and edge tables
CREATE TABLE Customer
   (
      ID INTEGER PRIMARY KEY,
      , CustomerName VARCHAR(100)
   )
   AS NODE;
CREATE TABLE Product
   (
      ID INTEGER PRIMARY KEY
      , ProductName VARCHAR(100)
   )
   AS NODE;
GO
CREATE TABLE bought
   (
      PurchaseCount INT
   )
   AS EDGE;
GO
ALTER TABLE bought ADD CONSTRAINT EC_BOUGHT1 CONNECTION (Customer TO Product);
```  

#### <a name="create-a-new-edge-constraint-on-existing-edge-table-with-additional-edge-constraint-clauses"></a>Создание ограничения ребра в существующей таблице ребер с использованием дополнительных предложений ограничения

В следующем примере используется команда `ALTER TABLE` для добавления нового ограничения ребра с дополнительными предложениями ограничения ребер в таблицу ребер **bought**.
  
```sql
-- CREATE node and edge tables
CREATE TABLE Customer
   (
      ID INTEGER PRIMARY KEY
      , CustomerName VARCHAR(100)
   )
   AS NODE;
GO
CREATE TABLE Supplier
   (
      ID INTEGER PRIMARY KEY
      , SupplierName VARCHAR(100)
   )
   AS NODE;
GO
CREATE TABLE Product
   (
      ID INTEGER PRIMARY KEY
      , ProductName VARCHAR(100)
   )
   AS NODE;
GO
CREATE TABLE bought
   (
      PurchaseCount INT
      , CONSTRAINT EC_BOUGHT CONNECTION (Customer TO Product)
   )
   AS EDGE;
-- Drop the existing edge constraint first and then create a new one.
ALTER TABLE bought DROP CONSTRAINT EC_BOUGHT;
GO
-- User ALTER TABLE to create a new edge constraint.
ALTER TABLE bought ADD CONSTRAINT EC_BOUGHT1 CONNECTION (Customer TO Product, Supplier TO Product);
```  

В предыдущем примере используются два предложения в ограничении *EC_BOUGHT1*: одно соединяет узел **Customer** с узлом **Product**, а другое — **Supplier** с **Product**. Оба этих предложения применены в логическом сложении. То есть заданное ребро должно соответствовать любому из этих двух предложений, чтобы использоваться в таблице ребер.

#### <a name="creating-a-new-edge-constraint-on-existing-edge-table-with-new-edge-constraint-clause"></a>Создание ограничения ребра в существующей таблице ребер с использованием нового предложения ограничения

В следующем примере используется команда `ALTER TABLE` для добавления нового ограничения ребра с новым предложением ограничения ребер в таблицу ребер **bought**.
  
 ```sql
-- CREATE node and edge tables
CREATE TABLE Customer
   (
      ID INTEGER PRIMARY KEY
      , CustomerName VARCHAR(100)
   )
   AS NODE;
GO
CREATE TABLE Supplier
   (
      ID INTEGER PRIMARY KEY
      , SupplierName VARCHAR(100)
   )
   AS NODE;
GO
CREATE TABLE Product
   (
      ID INTEGER PRIMARY KEY
      , ProductName VARCHAR(100)
   )
   AS NODE;
GO
CREATE TABLE bought
   (
      PurchaseCount INT,
         CONSTRAINT EC_BOUGHT CONNECTION (Customer TO Product)
   )
   AS EDGE;
GO
ALTER TABLE bought ADD CONSTRAINT EC_BOUGHT1 CONNECTION (Supplier TO Product);
 ```  

В предыдущем примере было создано два отдельных ограничения ребра в таблице ребер **bought**: *EC_BOUGHT* и *EC_BOUGHT1*. Оба этих ограничения имеют различные предложения ограничения ребра. Если в таблице ребер присутствует более одного ограничения, данное ребро должно соответствовать **ВСЕМ** ограничениям, чтобы использоваться в таблице ребер. Таблица ребер **bought** должна оставаться пустой, так как здесь ни одно ребро не удовлетворит *EC_BOUGHT* и *EC_BOUGHT1*.

Для успешного выполнения операции вставки в этой таблице ребер необходимо удалить одно ограничение ребра либо удалить оба ограничения и создать ограничение, в котором будут оба предложения ограничения ребер.

```sql
-- Drop the existing edge constraint first and then create a new one.
ALTER TABLE bought DROP CONSTRAINT EC_BOUGHT;
GO
ALTER TABLE bought DROP CONSTRAINT EC_BOUGHT1;
GO
ALTER TABLE bought ADD CONSTRAINT EC_BOUGHT_NEW CONNECTION (Customer TO Product, Supplier TO Product);
GO
```  

Чтобы заданное ребро было разрешено в таблице ребер **bought**, оно должно соответствовать всем предложениям в ограничении *EC_BOUGHT_NEW*. Таким образом, любое ребро, которое пытается соединить узел **Customer** с **Product** или **Supplier** с **Product**, будет разрешено.

### <a name="delete-edge-constraints"></a>Удаление ограничений ребер

В следующем примере сначала определяется имя ограничения ребер, а затем удаляется ограничение.  
  
```sql
-- CREATE node and edge tables
CREATE TABLE Customer
   (
      ID INTEGER PRIMARY KEY
      , CustomerName VARCHAR(100)
   )
   AS NODE;
GO
CREATE TABLE Product
   (
      ID INTEGER PRIMARY KEY
      , ProductName VARCHAR(100)
   ) AS NODE;
GO
CREATE TABLE bought
   (
      PurchaseCount INT
      , CONSTRAINT EC_BOUGHT CONNECTION (Customer TO Product)
    )
    AS EDGE;
GO
-- Return the name of edge constraint.
SELECT name  
   FROM sys.edge_constraints  
   WHERE type = 'EC' AND parent_object_id = OBJECT_ID('bought');  
GO  
-- Delete the primary key constraint.  
ALTER TABLE bought
DROP CONSTRAINT EC_BOUGHT;
```  

### <a name="modify-edge-constraints"></a>Изменение ограничений ребер

Чтобы изменить ограничение ребер с помощью Transact-SQL, необходимо сначала удалить имеющееся ограничение, а затем создать его повторно с помощью нового определения.


### <a name="view-edge-constraints"></a>Просмотр ограничений ребер

[!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).

В приведенном далее примере возвращаются сведения обо всех ограничениях ребер и их свойствах для таблицы ребер `bought` из базы данных tempdb.  

```sql
-- CREATE node and edge tables
CREATE TABLE Customer
   (
      ID INTEGER PRIMARY KEY
      , CustomerName VARCHAR(100)
   )
   AS NODE;
GO
CREATE TABLE Supplier
   (
      ID INTEGER PRIMARY KEY
      , SupplierName VARCHAR(100)
   )
   AS NODE;
   GO
CREATE TABLE Product
   (
      ID INTEGER PRIMARY KEY
      , ProductName VARCHAR(100)
   )
   AS NODE;

-- CREATE edge table with edge constraints.
CREATE TABLE bought
   (
      PurchaseCount INT
      , CONSTRAINT EC_BOUGHT CONNECTION (Customer TO Product, Supplier TO Product)
   )
   AS EDGE;

-- Query sys.edge_constraints and sys.edge_constraint_clauses to view
-- edge constraint properties.
SELECT
   EC.name AS edge_constraint_name
   , OBJECT_NAME(EC.parent_object_id) AS edge_table_name
   , OBJECT_NAME(ECC.from_object_id) AS from_node_table_name
   , OBJECT_NAME(ECC.to_object_id) AS to_node_table_name
   , is_disabled
   , is_not_trusted
FROM sys.edge_constraints EC
   INNER JOIN sys.edge_constraint_clauses ECC
   ON EC.object_id = ECC.object_id
WHERE EC.parent_object_id = object_id('bought');
```  

## <a name="related-tasks"></a>Связанные задачи

[CREATE TABLE (граф SQL)](../../t-sql/statements/create-table-sql-graph.md)  
[ALTER TABLE table_constraint](../../t-sql/statements/alter-table-table-constraint-transact-sql.md)  

Сведения о технологии графов в SQL Server см. в статье [Graph processing with SQL Server and Azure SQL Database](../graphs/sql-graph-overview.md?view=sql-server-2017) (Обработка графов с помощью SQL Server и Базы данных SQL Azure).

