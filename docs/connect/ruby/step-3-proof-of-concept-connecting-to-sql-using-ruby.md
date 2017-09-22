---
title: "Шаг 3: Эксперимент подключение к SQL с помощью Ruby | Документы Microsoft"
ms.custom: 
ms.date: 08/08/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cac20b18-0a6d-4243-bbda-a5d1b9476441
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: a645a57cac6eef7507aed9ea81df9fc75eb32dd4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/21/2017

---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-ruby"></a>Шаг 3: Эксперимент подключение к SQL с помощью Ruby

В этом примере следует рассматривать эксперимента только.  В образце кода упрощен для ясности и не представляет рекомендации рекомендуется корпорацией Майкрософт.  
  
## <a name="step-1--connect"></a>Шаг 1: подключение  
  
[TinyTDS::Client](https://github.com/rails-sqlserver/tiny_tds) функция используется для подключения к базе данных SQL.  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
```  
  
## <a name="step-2--execute-a-query"></a>Шаг 2: Выполнение запроса  
  
Скопируйте и вставьте следующий код в пустой файл. Вызовите test.rb. Затем выполните его, введя следующую команду в командной строке:  
  
    ruby test.rb  
  
В образце кода [TinyTds::Result](https://github.com/rails-sqlserver/tiny_tds) функция используется для получения результирующего набора из запроса к базе данных SQL. Эта функция принимает запрос и возвращает результирующий набор. Результирующий набор при итерации по строке с помощью [result.each сделать | строка |](https://github.com/rails-sqlserver/tiny_tds).  
  
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
  
## <a name="step-3--insert-a-row"></a>Шаг 3: Вставьте строку  
  
В этом примере показано, как выполнить [вставить](/sql-docs/docs/t-sql/statements/insert-transact-sql) инструкции безопасно, передавать параметры, которые защитить приложения от [атаки SQL injection](/sql-docs/docs/relational-databases/tables/primary-and-foreign-key-constraints) значение.    
  
Чтобы использовать TinyTDS с Azure, рекомендуется выполнить несколько `SET` инструкции для изменения способа обработки определенные сведения в текущем сеансе. Рекомендуется `SET` инструкции приведены в следующем образце кода. Например `SET ANSI_NULL_DFLT_ON` позволит новых столбцов, созданных допустимы значения null, даже если допустимость столбца не указан явно.  
  
Для выравнивания с Microsoft SQL Server [datetime](http://msdn.microsoft.com/library/ms187819.aspx) формат, используйте [strftime](http://ruby-doc.org/core-2.2.0/Time.html#method-i-strftime) функцию для приведения в соответствующий формат даты и времени.  
  
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

