---
title: Шаг 3. Подтверждение концепции, подразумевающее подключение к SQL с помощью pyodbc | Документация Майкрософт
ms.custom: ''
ms.date: 10/09/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4bfd6e52-817d-4f0a-a33d-11466e3f0484
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0e241d84ebc60acceafe09b1a9240711a72d2067
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "72798317"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>Шаг 3. Подтверждение концепции, подразумевающее подключение к SQL с помощью pyodbc

Этот пример следует рассматривать только как подтверждение концепции.  Пример кода упрощен для ясности и для него не гарантируется соблюдение рекомендаций корпорации Майкрософт.  

**Запустите пример скрипта, приведенный ниже**, создайте файл с именем test.py и добавляйте фрагменты кода по ходу работы. 

```
> python test.py
```
  
## <a name="step-1--connect"></a>Шаг 1.  Подключение  
  
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
  
  
## <a name="step-2--execute-query"></a>Шаг 2.  Выполнение запроса  
  
Функция cursor.execute может использоваться для извлечения результирующего набора из запроса к базе данных SQL. Эта функция фактически принимает любой запрос и возвращает результирующий набор, по которому может быть выполнена итерация с использованием cursor.fetchone().
  
  
```python
#Sample select query
cursor.execute("SELECT @@version;") 
row = cursor.fetchone() 
while row: 
    print(row[0])
    row = cursor.fetchone()

```  
  
## <a name="step-3--insert-a-row"></a>Шаг 3.  Вставка строки  
  
В этом примере вы увидите, как безопасно выполнить инструкцию [INSERT](../../../t-sql/statements/insert-transact-sql.md) и передать параметры для защиты приложения из значения [внедрения кода SQL](../../../relational-databases/tables/primary-and-foreign-key-constraints.md).    
  
  
```python

#Sample insert query
cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New 20', 'SQLEXPRESS New 20', 0, 0, CURRENT_TIMESTAMP )") 
cnxn.commit()
row = cursor.fetchone()

while row: 
    print 'Inserted Product key is ' + str(row[0]) 
    row = cursor.fetchone()
```  

## <a name="azure-active-directory-aad-and-the-connection-string"></a>Azure Active Directory (AAD) и строка подключения

pyODBC использует драйвер Microsoft ODBC для SQL Server.
Если ваша версия драйвера ODBC — 17.1 или более поздняя, интерактивный режим AAD драйвера ODBC можно использовать через pyODBC.
Этот интерактивный параметр AAD работает, если Python и pyODBC позволяют драйверу ODBC открывать диалоговое окно.
Этот параметр доступен только на ОС Windows.

### <a name="example-connection-string-for-aad-interactive-authentication"></a>Пример строки подключения для интерактивной проверки подлинности AAD

Ниже приведен пример строки подключения ODBC, в которой указывается интерактивная проверка подлинности AAD:

- `server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

Дополнительные сведения о параметрах проверки подлинности AAD для драйвера ODBC см. в следующей статье:

- [Использование Azure Active Directory с драйвером ODBC](../../odbc/using-azure-active-directory.md#new-andor-modified-dsn-and-connection-string-keywords)

## <a name="next-steps"></a>Дальнейшие действия
  
Дополнительную информацию можно найти в [Центре разработчика Python](https://azure.microsoft.com/develop/python/).
