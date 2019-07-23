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
ms.openlocfilehash: 27b56a20a0456bef04553c614432bde270d8e98d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67935775"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pymssql"></a>Шаг 3. Подтверждение концепции, подразумевающее подключение к SQL с помощью pymssql
[!INCLUDE[Driver_Python_Download](../../../includes/driver_python_download.md)]

Этот пример следует рассматривать только для подтверждения концепции.  Пример кода упрощен для ясности и не обязательно представляет лучшие методики, рекомендованные корпорацией Майкрософт.  
  
## <a name="step-1--connect"></a>Шаг 1. подключение  
  
Функция [pymssql. Connect](https://pymssql.org/en/latest/ref/pymssql.html) используется для подключения к базе данных SQL.  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
```  
  
  
## <a name="step-2--execute-query"></a>Шаг 2. выполнение запроса  
  
Функцию [cursor. Execute](https://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.execute) можно использовать для получения результирующего набора из запроса к базе данных SQL. Эта функция по сути принимает любой запрос и возвращает результирующий набор, для которого можно выполнить итерацию с использованием [cursor. fetchone ()](https://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.fetchone).  
  
  
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
  
## <a name="step-3--insert-a-row"></a>Шаг 3. Вставка строки  
  
В этом примере вы узнаете, как безопасно выполнить инструкцию [INSERT](../../../t-sql/statements/insert-transact-sql.md) , передав параметры, которые защищают приложение от [внедрения кода SQL](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) .    
  
  
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
  
## <a name="step-4--rollback-a-transaction"></a>Шаг 4. откат транзакции  
  
В этом примере кода показано использование транзакций, в которых вы:  
  
* Начать транзакцию  
* Вставка строки данных  
* Откатить транзакцию для отмены вставки  
  
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
  
Дополнительные сведения см. в [центре разработчиков Python](https://azure.microsoft.com/develop/python/).
