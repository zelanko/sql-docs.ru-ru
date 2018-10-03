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
manager: craigg
ms.openlocfilehash: cd861c50523e218bc1cf0ed6e538e66eeb3671f3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47756317"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>Шаг 3. Эксперимент, подразумевающий подключение к SQL с помощью pyodbc

В этом примере следует рассматривать подтверждение концепции только.  Пример кода упрощен для ясности и не всегда представляет рекомендации, рекомендуемые корпорацией Майкрософт.  

**Запустите пример сценария ниже** создайте файл с именем test.py и добавьте каждого фрагмента кода в ходе работы. 

```
> python test.py
```
  
## <a name="step-1--connect"></a>Шаг 1: подключение  
  
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
  
  
## <a name="step-2--execute-query"></a>Шаг 2: Выполнение запроса  
  
Cursor.executefunction может использоваться для извлечения результирующего набора из запроса к базе данных SQL. Эта функция фактически принимает любой запрос и возвращает результирующий набор, который может быть выполнена итерация с использованием cursor.fetchone()
  
  
```python
#Sample select query
cursor.execute("SELECT @@version;") 
row = cursor.fetchone() 
while row: 
    print row[0] 
    row = cursor.fetchone()

```  
  
## <a name="step-3--insert-a-row"></a>Шаг 3: Вставка строки  
  
В этом примере показано, как выполнить [вставить](../../../t-sql/statements/insert-transact-sql.md) инструкции безопасно, передать параметры для защиты от атак [путем внедрения кода SQL](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) значение.    
  
  
```python

#Sample insert query
cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New 20', 'SQLEXPRESS New 20', 0, 0, CURRENT_TIMESTAMP )") 
row = cursor.fetchone()

while row: 
    print 'Inserted Product key is ' + str(row[0]) 
    row = cursor.fetchone()
```  
  `      
  ## <a name="next-steps"></a>Следующие шаги  
  
Дополнительные сведения см. в разделе [Центр разработчиков Python](https://azure.microsoft.com/develop/python/).
