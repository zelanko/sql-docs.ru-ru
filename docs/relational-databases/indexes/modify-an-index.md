---
title: "Изменение индекса | Microsoft Docs"
ms.custom: ""
ms.date: "02/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-indexes"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "индексы [SQL Server], изменение"
  - "изменение индексов"
  - "изменения индекса [SQL Server]"
ms.assetid: 97e3110d-fde7-4f5d-9309-dc1697960aeb
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# Изменение индекса
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  В этом разделе описывается изменение индекса в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!IMPORTANT]  
>  Индексы, созданные в результате применения ограничения PRIMARY KEY или UNIQUE, изменить этим способом нельзя. Вместо этого необходимо изменить ограничение.  
  
 **В этом разделе**  
  
-   **Для изменения индекса используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Изменение индекса  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Разверните **Базы данных**, затем базу данных, которой принадлежит таблица, и **Таблицы**.  
  
3.  Раскройте таблицу, которой принадлежит индекс, а затем — узел **Индексы**.  
  
4.  Щелкните правой кнопкой мыши индекс, который нужно изменить, и выберите пункт **Свойства**.  
  
5.  В диалоговом окне **Свойства индекса** внесите необходимые изменения. Например, можно добавить или удалить столбец из ключа индекса или изменить значение параметра индекса.  
  
#### Изменение столбцов индекса  
  
1.  Чтобы добавить столбец индекса, удалить его или изменить его позицию, выберите в диалоговом окне **Свойства индекса** страницу **Общие** .  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Изменение индекса  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере индекс по столбцу `ProductID` таблицы `Production.WorkOrder` удаляется и создается вновь с помощью параметра `DROP_EXISTING`. Указываются также аргументы `FILLFACTOR` и `PAD_INDEX`.  
  
     [!code-sql[IndexDDL#CreateIndex4](../../relational-databases/indexes/codesnippet/tsql/modify-an-index_1.sql)]  
  
     В следующем примере с помощью инструкции ALTER INDEX задаются несколько параметров для индекса `AK_SalesOrderHeader_SalesOrderNumber`.  
  
     [!code-sql[IndexDDL#AlterIndex4](../../relational-databases/indexes/codesnippet/tsql/modify-an-index_2.sql)]  
  
#### Изменение столбцов индекса  
  
1.  Чтобы добавить, удалить или изменить позицию столбца индекса, необходимо удалить и повторно создать индекс.  
  
## См. также:  
 [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)   
 [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md)   
 [INDEXPROPERTY (Transact-SQL)](../../t-sql/functions/indexproperty-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [Установка параметров индекса](../../relational-databases/indexes/set-index-options.md)   
 [Переименование индексов](../../relational-databases/indexes/rename-indexes.md)  
  
  