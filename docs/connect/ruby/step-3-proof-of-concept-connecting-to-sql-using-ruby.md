---
title: 'Шаг 3. Подтверждение концепции: подключение к SQL с помощью Ruby | Документация Майкрософт'
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
ms.openlocfilehash: 9724fb48f6ae896d9026bfec63056070e2180a8e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67992489"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-ruby"></a>Шаг 3. Подтверждение концепции, подразумевающее подключение к SQL с помощью PHP

Этот пример следует рассматривать только как подтверждение концепции.  Пример кода упрощен для ясности и для него не гарантируется соблюдение рекомендаций корпорации Майкрософт.  
  
## <a name="step-1--connect"></a>Шаг 1.  Подключение  
  
Функция [TinyTDS::Client](https://github.com/rails-sqlserver/tiny_tds) используется для подключения к Базе данных SQL.  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
```  
  
## <a name="step-2--execute-a-query"></a>Шаг 2.  Выполнение запроса  
  
Скопируйте следующий код и вставьте его в пустой файл. Назовите его test.rb. Затем выполните его, введя следующую команду в командной строке:  
  
    ruby test.rb  
  
В примере кода функция [TinyTds::Result](https://github.com/rails-sqlserver/tiny_tds) используется для извлечения результирующего набора из запроса к базе данных SQL. Эта функция принимает запрос и возвращает результирующий набор. По результирующему набору выполняется итерация с помощью [result.each do |row|](https://github.com/rails-sqlserver/tiny_tds).  
  
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
  
## <a name="step-3--insert-a-row"></a>Шаг 3.  Вставка строки  
  
В этом примере вы увидите, как безопасно выполнить инструкцию [INSERT](../../t-sql/statements/insert-transact-sql.md) и передать параметры для защиты приложения из значения [внедрения кода SQL](../../relational-databases/tables/primary-and-foreign-key-constraints.md).    
  
Чтобы использовать TinyTDS с Azure, рекомендуем выполнить несколько инструкций `SET` , чтобы изменить способ обработки определенной информации в текущем сеансе. Рекомендуемые инструкции `SET` предоставлены в примере кода. Например, инструкция `SET ANSI_NULL_DFLT_ON` позволяет использовать нулевые значения в новых столбцах, даже если допустимость нулевых значений в столбце не указана явным образом.  
  
Для согласования с форматом [datetime](../../t-sql/data-types/datetime-transact-sql.md) Microsoft SQL Server используйте функцию [strftime](https://ruby-doc.org/core-2.2.0/Time.html#method-i-strftime), чтобы привести дату и время к соответствующему формату.  
  
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
