---
description: Выполнение определяемых пользователем функций
title: Выполнение определяемых пользователем функций | Документация Майкрософт
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- invoking user-defined functions
- user-defined functions [SQL Server], executing
ms.assetid: 0de7744d-9b73-463f-ae80-e31a020004b5
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: dc0904609ba680ae25c26e529fb49d328d310a77
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97484396"
---
# <a name="execute-user-defined-functions"></a>Выполнение определяемых пользователем функций
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Выполните определяемую пользователем функцию с помощью Transact-SQL.
  

> **Примечание.** Дополнительные сведения см. в разделах, посвященных  [определяемым пользователем функциям](user-defined-functions.md) и [созданию функций (Transact SQL](../../t-sql/statements/create-function-transact-sql.md) . 
  
 
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 В Transact-SQL параметры могут передаваться через *value* или с помощью @*parameter_name*=*value.* . Параметр не является частью транзакции, поэтому если он изменился в транзакции, которая впоследствии подверглась откату, то прежнее значение параметра не восстанавливается. Возвращаемым вызывающему значением всегда является то значение, которое существует на момент выхода из модуля.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
 На выполнение инструкции [EXECUTE](../../t-sql/language-elements/execute-transact-sql.md) разрешения не требуются. Однако **необходимы** разрешения на защищаемые объекты, на которые ссылается командная строка в инструкции EXECUTE. Например, если строка содержит инструкцию [INSERT](../../t-sql/statements/insert-transact-sql.md) , вызывающий инструкцию EXECUTE пользователь должен иметь разрешение INSERT на целевую таблицу. Разрешения проверяются в месте нахождения инструкции EXECUTE, даже если она содержится внутри модуля. Дополнительные сведения см. в разделе [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
### <a name="example"></a>Пример 
  
В этом примере используется скалярная функция `ufnGetSalesOrderStatusText` , которая доступна в большинстве выпусков `AdventureWorks`.  Функция предназначена для возврата текстового значения для состояния продаж из заданного целого числа.  Измените пример, передавая целые числа от 1 до 7 в параметр **\@Status** .
  
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
  
  
  
