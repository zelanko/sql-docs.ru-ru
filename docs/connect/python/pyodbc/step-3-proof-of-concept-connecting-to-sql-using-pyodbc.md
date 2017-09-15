---
title: "Шаг 3: Эксперимент подключение к SQL с помощью pyodbc | Документы Microsoft"
ms.custom: 
ms.date: 08/08/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bfd6e52-817d-4f0a-a33d-11466e3f0484
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b71b6e4f40e4f1910d825071b8a0d86db4987624
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>Шаг 3: Эксперимент подключение к SQL с помощью pyodbc

В этом примере следует рассматривать эксперимента только.  В образце кода упрощен для ясности и не представляет рекомендации рекомендуется корпорацией Майкрософт.  

**Запустите образец скрипта ниже** создайте файл с именем test.py и добавьте каждый фрагмент кода, при переходе. 

```
> python test.py
```
  
## <a name="step-1--connect"></a>Шаг 1: подключение  
  
```python

import pyodbc 
server = 'tcp:myserver.database.windows.net' 
database = 'mydb' 
username = 'myusername' 
password = 'mypassword' 
cnxn = pyodbc.connect('DRIVER={ODBC Driver 13 for SQL Server};SERVER='+server+';DATABASE='+database+';UID='+username+';PWD='+ password)
cursor = cnxn.cursor()

```  
  
  
## <a name="step-2--execute-query"></a>Шаг 2: Выполнение запроса  
  
Cursor.executefunction можно использовать для извлечения результирующего набора из запроса к базе данных SQL. По существу эта функция принимает любой запрос и возвращает результирующий набор, который может быть выполнен обход с использованием cursor.fetchone()
  
  
```python
#Sample select query
cursor.execute("SELECT @@version;") 
row = cursor.fetchone() 
while row: 
    print row[0] 
    row = cursor.fetchone()

```  
  
## <a name="step-3--insert-a-row"></a>Шаг 3: Вставьте строку  
  
В этом примере показано, как выполнить [вставить](https://msdn.microsoft.com/library/ms174335.aspx) инструкции безопасно, передавать параметры, которые защитить приложения от [путем внедрения кода SQL](https://technet.microsoft.com/library/ms161953(v=sql.105).aspx) уязвимости и извлечь создан[Первичного ключа](https://msdn.microsoft.com/library/ms179610.aspx) значение.    
  
  
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
  
Дополнительные сведения см. в разделе [центре разработчиков Python](https://azure.microsoft.com/en-us/develop/python/).
