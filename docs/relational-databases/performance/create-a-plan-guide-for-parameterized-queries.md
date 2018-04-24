---
title: Создание структуры плана для параметризованных запросов | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: performance
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-plan-guides
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameterized queries, plan guides for
- plan guides [SQL Server], parameterized queries
ms.assetid: b532ae16-66e7-4641-9bc8-b0d805853477
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a98c7b2567d500c006aec5799e36fc0955e4c61e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-plan-guide-for-parameterized-queries"></a>Создание руководства плана для параметризованных запросов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Структура плана TEMPLATE соответствует изолированным инструкциям с параметрами.  
  
 В приведенном ниже примере создается структура плана, которой сопоставляется запрос заданной параметризованной формы и которое вынуждает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметризовать поступающие запросы. Два приведенных ниже запроса являются синтаксическими эквивалентами, однако различаются своими значениями постоянных литералов.  
  
```  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45639;  
  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45640;  
```  
  
 Ниже представлена структура плана для параметризованного запроса.  
  
```  
EXEC sp_create_plan_guide   
    @name = N'TemplateGuide1',  
    @stmt = N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
              INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
                  ON h.SalesOrderID = d.SalesOrderID  
              WHERE h.SalesOrderID = @0',  
    @type = N'TEMPLATE',  
    @module_or_batch = NULL,  
    @params = N'@0 int',  
    @hints = N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
 В предыдущем примере значение параметра `@stmt` является параметризованной формой запроса. Единственным надежным способом выяснения указанного значения для использования в процедуре sp_create_plan_guide является использование системной хранимой процедуры [sp_get_query_template](../../relational-databases/system-stored-procedures/sp-get-query-template-transact-sql.md) . Следующий скрипт можно использовать как для получения параметризированного запроса, так и для дальнейшего создания по нему структуры плана:  
  
```  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
      INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
          ON h.SalesOrderID = d.SalesOrderID  
      WHERE h.SalesOrderID = 45639;',  
    @stmt OUTPUT,   
    @params OUTPUT  
EXEC sp_create_plan_guide N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
> [!IMPORTANT]  
>  Значения постоянных литералов аргумента `@stmt` , передаваемого в процедуру `sp_get_query_template` , определяют тип данных для аргумента, заменяющего указанные литералы. Это влияет на совпадение структур планов. Возможно, придется создать несколько структур плана для обработки различных диапазонов значений аргумента.  
  
 Структуры планов TEMPLATE также можно использовать совместно со структурами планов SQL. Например, можно создать структуру плана TEMPLATE, чтобы убедиться, что класс запросов будет параметризован. Затем можно создать руководство плана SQL для параметризованной формы запроса.  
  
  
