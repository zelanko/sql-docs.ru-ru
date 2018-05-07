---
title: 'Шаг 3: Эксперимент подключение к SQL с помощью pyodbc | Документы Microsoft'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: python
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4bfd6e52-817d-4f0a-a33d-11466e3f0484
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b11b11689ecccb7e63d003a3b35eebbca951f08f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
В этом примере показано, как выполнить [вставить](../../../t-sql/statements/insert-transact-sql.md) инструкции безопасно, передавать параметры, которые защитить приложения от [атаки SQL injection](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) значение.    
  
  
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
