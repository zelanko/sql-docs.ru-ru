---
title: Шаг 3. Подтверждение концепции, подразумевающее подключение к SQL с помощью pymssql | Документация Майкрософт
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
ms.openlocfilehash: c1dfce515eeadbdbaf1fd96e6dcf1a08cd536ab5
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "74200459"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pymssql"></a>Шаг 3. Подтверждение концепции, подразумевающее подключение к SQL с помощью pymssql
[!INCLUDE[Driver_Python_Download](../../../includes/driver_python_download.md)]

Этот пример следует рассматривать только как подтверждение концепции.  Пример кода упрощен для ясности и он не обязательно рекомендуется к использованию корпорацией Майкрософт.  
  
## <a name="step-1--connect"></a>Шаг 1.  Подключение  
  
Функция [pymssql.connect](https://pypi.org/project/pymssql/) используется для подключения к базе данных SQL.  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
```  
  
  
## <a name="step-2--execute-query"></a>Шаг 2.  Выполнение запроса  
  
Функция [cursor.execute](https://pypi.org/project/pymssql/) может использоваться для извлечения результирующего набора из запроса к базе данных SQL. Эта функция фактически принимает любой запрос и возвращает результирующий набор, по которому может быть выполнена итерация с использованием [cursor.fetchone()](https://pypi.org/project/pymssql/).  
  
  
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
  
## <a name="step-3--insert-a-row"></a>Шаг 3.  Вставка строки  
  
В этом примере показано, как безопасно выполнить инструкцию [INSERT](../../../t-sql/statements/insert-transact-sql.md) и передать параметры для защиты от [внедрения кода SQL](../../../relational-databases/tables/primary-and-foreign-key-constraints.md).    
  
  
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
  
## <a name="step-4--rollback-a-transaction"></a>Шаг 4.  Откат транзакции  
  
Этот пример кода демонстрирует использование транзакций, в которых можно:  
  
* начать транзакцию;  
* вставить строку данных;  
* откатить транзакцию для отмены вставки.  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute("BEGIN TRANSACTION")  
    cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New', 'SQLEXPRESS New', 0, 0, CURRENT_TIMESTAMP)")  
    conn.rollback()  
    conn.close()
```  
    
  ## <a name="next-steps"></a>Дальнейшие действия  
  
Дополнительную информацию можно найти в [Центре разработчика Python](https://azure.microsoft.com/develop/python/).
