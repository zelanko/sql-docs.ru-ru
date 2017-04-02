---
title: "Выполнение определяемых пользователем функций | Microsoft Docs"
ms.custom: ""
ms.date: "10/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-udf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "вызов определяемых пользователем функций"
  - "user-defined functions [SQL Server], executing"
ms.assetid: 0de7744d-9b73-463f-ae80-e31a020004b5
caps.latest.revision: 35
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 35
---
# Выполнение определяемых пользователем функций
  Выполните определяемую пользователем функцию с помощью Transact-SQL.
  

> **Примечание.** Дополнительные сведения см. в разделах, посвященных [определяемым пользователем функциям](https://msdn.microsoft.com/library/ms191007.aspx) и [созданию функций (Transact SQL](https://msdn.microsoft.com/library/ms186755.aspx). 
  
 
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 В Transact-SQL параметры могут передаваться через *value* или с помощью @*parameter_name*=*value.* . Параметр не является частью транзакции, поэтому если он изменился в транзакции, которая впоследствии подверглась откату, то прежнее значение параметра не восстанавливается. Возвращаемым вызывающему значением всегда является то значение, которое существует на момент выхода из модуля.  
  
###  <a name="Security"></a> Безопасность  
  
 На выполнение инструкции [EXECUTE](https://msdn.microsoft.com/library/ms188332.aspx) разрешения не требуются. Однако **необходимы** разрешения на защищаемые объекты, на которые ссылается командная строка в инструкции EXECUTE. Например, если строка содержит инструкцию [INSERT](https://msdn.microsoft.com/library/ms174335.aspx), вызывающий инструкцию EXECUTE пользователь должен иметь разрешение INSERT на целевую таблицу. Разрешения проверяются в месте нахождения инструкции EXECUTE, даже если она содержится внутри модуля. Дополнительные сведения см. в разделе [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
### Пример 
  
В этом примере используется скалярная функция `ufnGetSalesOrderStatusText`, которая доступна в большинстве выпусков `AdventureWorks`.  Функция предназначена для возврата текстового значения для состояния продаж из заданного целого числа.  Измените пример, передавая целые числа от 1 до 7 в параметр **\@Status**.
  
~~~tsql
USE [AdventureWorks2016CTP3]
GO  

-- Declare a variable to return the results of the function. 
DECLARE @ret nvarchar(15);   

-- Execute the function while passing a value to the @status parameter
EXEC @ret = dbo.ufnGetSalesOrderStatusText 
    @Status = 5; 

-- View the returned value.  The Execute and Select statements must be executed at the same time.  
SELECT N'Order Status: ' + @ret; 

-- Result:
-- Order Status: Shipped
~~~
  
  
  