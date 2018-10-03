---
title: Шаг 3. Подтверждение концепции, подразумевающее подключение к SQL с помощью pymssql | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2246ddeb-7c2f-46f3-8a91-cdd718d39b40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 81042ababad2b8ec7107a4413dfd6e3dcecafb8c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764062"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pymssql"></a>Шаг 3. Подтверждение концепции, подразумевающее подключение к SQL с помощью pymssql
[!INCLUDE[Driver_Python_Download](../../../includes/driver_python_download.md)]

В этом примере следует рассматривать подтверждение концепции только.  Пример кода упрощен для ясности и не всегда представляет рекомендации, рекомендуемые корпорацией Майкрософт.  
  
## <a name="step-1--connect"></a>Шаг 1: подключение  
  
[Pymssql.connect](http://pymssql.org/en/latest/ref/pymssql.html) функция используется для подключения к базе данных SQL.  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
```  
  
  
## <a name="step-2--execute-query"></a>Шаг 2: Выполнение запроса  
  
[Cursor.execute](http://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.execute) функция может использоваться для извлечения результирующего набора из запроса к базе данных SQL. Эта функция фактически принимает любой запрос и возвращает результирующий набор, который может быть выполнена итерация с использованием [cursor.fetchone()](http://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.fetchone).  
  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute('SELECT c.CustomerID, c.CompanyName,COUNT(soh.SalesOrderID) AS OrderCount FROM SalesLT.Customer AS c LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh ON c.CustomerID = soh.CustomerID GROUP BY c.CustomerID, c.CompanyName ORDER BY OrderCount DESC;')  
    row = cursor.fetchone()  
    while row:  
        print str(row[0]) + " " + str(row[1]) + " " + str(row[2])     
        row = cursor.fetchone()  
```  
  
## <a name="step-3--insert-a-row"></a>Шаг 3: Вставка строки  
  
В этом примере показано, как выполнить [вставить](../../../t-sql/statements/insert-transact-sql.md) инструкции безопасно, передать параметры для защиты от атак [путем внедрения кода SQL](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) значение.    
  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express', 'SQLEXPRESS', 0, 0, CURRENT_TIMESTAMP)")  
    row = cursor.fetchone()  
    while row:  
        print "Inserted Product ID : " +str(row[0])  
        row = cursor.fetchone()  
    conn.commit()
    conn.close()
```  
  
## <a name="step-4--rollback-a-transaction"></a>Шаг 4: Выполнить откат транзакции  
  
Этот пример кода демонстрирует использование транзакций, в котором вы:  
  
* Начать транзакцию  
* Вставить строку данных  
* Откат транзакции для отмены вставки  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute("BEGIN TRANSACTION")  
    cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New', 'SQLEXPRESS New', 0, 0, CURRENT_TIMESTAMP)")  
    conn.rollback()  
    conn.close()
```  
    
  ## <a name="next-steps"></a>Следующие шаги  
  
Дополнительные сведения см. в разделе [Центр разработчиков Python](https://azure.microsoft.com/develop/python/).
