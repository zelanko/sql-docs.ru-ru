---
title: Шаг 3. Подтверждение концепции, подразумевающее подключение к SQL с помощью pyodbc | Документы Майкрософт
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4bfd6e52-817d-4f0a-a33d-11466e3f0484
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 30ba3db5e23d95128aecbb5cc8974faeb6d58d75
ms.sourcegitcommit: 6413b7495313830ad1ae5aefe0c09e8e7a284b07
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 09/16/2019
ms.locfileid: "71016843"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>Шаг 3. Эксперимент, подразумевающий подключение к SQL с помощью pyodbc

Этот пример следует рассматривать только для подтверждения концепции.  Пример кода упрощен для ясности и не обязательно представляет лучшие методики, рекомендованные корпорацией Майкрософт.  

**Запустить пример скрипта ниже**  Создайте файл с именем test.py и добавьте каждый фрагмент кода по ходу его. 

```
> python test.py
```
  
## <a name="step-1--connect"></a>Шаг 1. подключение  
  
```python

import pyodbc 
# Some other example server values are
# server = 'localhost\sqlexpress' # for a named instance
# server = 'myserver,port' # to specify an alternate port
server = 'tcp:myserver.database.windows.net' 
database = 'mydb' 
username = 'myusername' 
password = 'mypassword' 
cnxn = pyodbc.connect('DRIVER={ODBC Driver 17 for SQL Server};SERVER='+server+';DATABASE='+database+';UID='+username+';PWD='+ password)
cursor = cnxn.cursor()

```  
  
  
## <a name="step-2--execute-query"></a>Шаг 2. выполнение запроса  
  
Cursor. ExecuteFunction можно использовать для получения результирующего набора из запроса к базе данных SQL. Эта функция по сути принимает любой запрос и возвращает результирующий набор, для которого можно выполнить итерацию с использованием Cursor. fetchone ().
  
  
```python
#Sample select query
cursor.execute("SELECT @@version;") 
row = cursor.fetchone() 
while row: 
    print row[0] 
    row = cursor.fetchone()

```  
  
## <a name="step-3--insert-a-row"></a>Шаг 3. Вставка строки  
  
В этом примере вы узнаете, как безопасно выполнить инструкцию [INSERT](../../../t-sql/statements/insert-transact-sql.md) , передав параметры, которые защищают приложение от [внедрения кода SQL](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) .    
  
  
```python

#Sample insert query
cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New 20', 'SQLEXPRESS New 20', 0, 0, CURRENT_TIMESTAMP )") 
cnxn.commit()
row = cursor.fetchone()

while row: 
    print 'Inserted Product key is ' + str(row[0]) 
    row = cursor.fetchone()
```  
  `      
  ## <a name="next-steps"></a>Следующие шаги  
  
Дополнительные сведения см. в [центре разработчиков Python](https://azure.microsoft.com/develop/python/).
