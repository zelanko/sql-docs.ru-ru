---
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
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ae608ebf733857cf086f4953a6d75dd75eadc5ae
ms.sourcegitcommit: b1990ec4491b5a8097c3675334009cb2876673ef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2018
ms.locfileid: "49384119"
---
# <a name="create-primary-keys"></a>Создание первичных ключей
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Определить первичный ключ в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Создание первичного ключа автоматически приводит к созданию соответствующего уникального кластеризованного индекса (или некластеризованного при наличии такого указания).  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   В таблице возможно наличие только одного ограничения по первичному ключу.  
  
-   Все столбцы с ограничением PRIMARY KEY должны иметь признак NOT NULL. Если допустимость значения NULL не указана, то для всех столбцов c ограничением PRIMARY KEY устанавливается признак NOT NULL.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Создание новой таблицы с первичным ключом требует разрешения CREATE TABLE в базе данных и разрешения ALTER на схему, в которой создается таблица.  
  
 Создание первичного ключа в существующей таблице требует разрешения ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-primary-key"></a>Создание первичного ключа  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши таблицу, в которую необходимо добавить ограничение уникальности, и выберите **Конструктор**.  
  
2.  В **Конструкторе таблиц**щелкните селектор строк для столбца базы данных, который необходимо определить в качестве первичного ключа. Чтобы выделить несколько столбцов, нажмите и удерживайте клавишу CTRL и щелкните селекторы строк для остальных столбцов.  
  
3.  Щелкните правой кнопкой мыши средство выбора строк столбца и выберите команду **Задать первичный ключ**.  
  
> [!CAUTION]  
>  Чтобы переопределить первичный ключ, необходимо удалить все связи с существующим первичным ключом и только после этого создавать новый первичный ключ. Появится сообщение, предупреждающее об автоматическом удалении в ходе процесса всех существующих связей.  
  
 Ключевой столбец-источник идентифицируется символом первичного ключа в соответствующем селекторе строк.  
  
 Если первичный ключ состоит более чем из одного столбца, то в одном столбце могут встречаться дублирующиеся значения, но все сочетания значений изо всех столбцов первичного ключа должны быть уникальными.  
  
 При определении составного ключа порядок столбцов в первичном ключе совпадает с порядком столбцов, показанным в таблице. Однако после создания первичного ключа порядок столбцов можно изменить. Дополнительные сведения см. в разделе [Изменение первичных ключей](../../relational-databases/tables/modify-primary-keys.md).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  

### <a name="to-create-a-primary-key-in-an-existing-table"></a>Создание первичного ключа в существующей таблице  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере создается первичный ключ в столбце `TransactionID`.  
  
    ```sql  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Production.TransactionHistoryArchive   
    ADD CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID);  
    GO  
    ```  
  
### <a name="to-create-a-primary-key-in-a-new-table"></a>Создание первичного ключа в новой таблице  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере создается таблица и определяется первичный ключ для столбца `TransactionID`.  
  
    ```sql  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive1  
    (  
       TransactionID int IDENTITY (1,1) NOT NULL,  
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID)  
    );  
    GO  
    ```  

### <a name="to-create-a-primary-key-with-nonclustered-index-in-a-new-table"></a>Создание первичного ключа с некластеризованным индексом в новой таблице  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере создается таблица и определяется первичный ключ для столбца `CustomerID` и кластеризованный индекс для `TransactionID`.  
  
    ```sql  
    -- Select appropriate database
    USE AdventureWorks2012;  
    GO  
    -- Create table to add the clustered index
    CREATE TABLE Production.TransactionHistoryArchive1  
    (  
       CustomerID uniqueidentifier DEFAULT NEWSEQUENTIALID(),
       TransactionID int IDENTITY (1,1) NOT NULL,  
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY NONCLUSTERED (uniqueidentifier)  
    );  
    GO  

    -- Now add the clustered index
    CREATE CLUSTERED INDEX CIX_TransactionID ON Production.TransactionHistoryArchive1 (TransactionID);
    GO
    ```  

## <a name="see-also"></a>См. также:    
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)    
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)     
[table_constraint &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-table-constraint-transact-sql.md)    
