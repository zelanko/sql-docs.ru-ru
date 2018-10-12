---
title: Шаг 3. Эксперимент, подразумевающий подключение к SQL с помощью Ruby | Документация Майкрософт
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cac20b18-0a6d-4243-bbda-a5d1b9476441
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9eed37349152b48ab49859b44cc23cb463d8541b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47801382"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-ruby"></a>Шаг 3. Эксперимент, подразумевающий подключение к SQL с помощью Ruby

В этом примере следует рассматривать подтверждение концепции только.  Пример кода упрощен для ясности и не всегда представляет рекомендации, рекомендуемые корпорацией Майкрософт.  
  
## <a name="step-1--connect"></a>Шаг 1: подключение  
  
[TinyTDS::Client](https://github.com/rails-sqlserver/tiny_tds) функция используется для подключения к базе данных SQL.  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
```  
  
## <a name="step-2--execute-a-query"></a>Шаг 2. Выполнение запроса  
  
Скопируйте и вставьте следующий код в пустой файл. Назовите его test.rb. Затем выполните его, введя следующую команду в командной строке:  
  
    ruby test.rb  
  
В образце кода [TinyTds::Result](https://github.com/rails-sqlserver/tiny_tds) функция используется для извлечения результирующего набора из запроса к базе данных SQL. Эта функция принимает запрос и возвращает результирующий набор. Набор результатов выполняется итерация с помощью [result.each do | строка |](https://github.com/rails-sqlserver/tiny_tds).  
  
``` ruby 
    require 'tiny_tds'    
    print 'test'       
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
    results = client.execute("SELECT c.CustomerID, c.CompanyName,COUNT(soh.SalesOrderID) AS OrderCount FROM SalesLT.Customer AS c LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh ON c.CustomerID = soh.CustomerID GROUP BY c.CustomerID, c.CompanyName ORDER BY OrderCount DESC")  
    results.each do |row|  
    puts row  
    end  
```  
  
## <a name="step-3--insert-a-row"></a>Шаг 3: Вставка строки  
  
В этом примере показано, как выполнить [вставить](../../t-sql/statements/insert-transact-sql.md) инструкции безопасно, передать параметры для защиты от атак [путем внедрения кода SQL](../../relational-databases/tables/primary-and-foreign-key-constraints.md) значение.    
  
Чтобы использовать TinyTDS с Azure, рекомендуется выполнить несколько `SET` инструкции, чтобы изменить способ обработки определенной информации в текущий сеанс. Рекомендуется `SET` инструкции приведены в следующем образце кода. Например `SET ANSI_NULL_DFLT_ON` позволит новых столбцов, созданных допустимы значения null, даже если допустимость нулевых значений в столбце не указана явным образом.  
  
В соответствии с Microsoft SQL Server [datetime](../../t-sql/data-types/datetime-transact-sql.md) форматирования, используйте [strftime](http://ruby-doc.org/core-2.2.0/Time.html#method-i-strftime) функция для приведения в соответствующий формат даты и времени.  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
    results = client.execute("SET ANSI_NULLS ON")  
    results = client.execute("SET CURSOR_CLOSE_ON_COMMIT OFF")  
    results = client.execute("SET ANSI_NULL_DFLT_ON ON")  
    results = client.execute("SET IMPLICIT_TRANSACTIONS OFF")  
    results = client.execute("SET ANSI_PADDING ON")  
    results = client.execute("SET QUOTED_IDENTIFIER ON")  
    results = client.execute("SET ANSI_WARNINGS ON")  
    results = client.execute("SET CONCAT_NULL_YIELDS_NULL ON")  
    require 'date'  
    t = Time.now  
    curr_date = t.strftime("%Y-%m-%d %H:%M:%S.%L")  
    results = client.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate)  
    OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New', 'SQLEXPRESS New', 0, 0, '#{curr_date}' )")  
    results.each do |row|  
    puts row  
    end  
```
