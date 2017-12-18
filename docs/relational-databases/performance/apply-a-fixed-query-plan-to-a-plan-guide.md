---
title: "Применение фиксированного плана запроса к структуре плана | Документация Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-plan-guides
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbf401f9-af7c-48e7-8a43-bf25e8af2fd7
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f81b0d8ea6fb5fa3b6ae954f6d2b2a67cea6fd7e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="apply-a-fixed-query-plan-to-a-plan-guide"></a>Применение фиксированного плана запроса к структуре плана
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Вы можете применить фиксированный план запроса к структуре плана типа OBJECT или SQL. Структуры планов, применяющие фиксированные планы запроса, удобно использовать в тех случаях, когда известно, что есть план выполнения, который работает с большей производительностью, чем выбранный оптимизатором для конкретного запроса.  
  
 В следующем примере создается структура плана для простой нерегламентированной инструкции SQL. Требуемый план запроса для этого оператора представлен в структуре плана путем указания XML Showplan для запроса непосредственно в параметре `@hints` . В примере сначала выполняется инструкция SQL для создания плана в кэше планов. В этом примере допустим, что созданный план является желаемым планом и не требуется дополнительной настройки запросов. Данные XML Showplan для запроса необходимо получить с помощью запроса к динамическим административным представлениям `sys.dm_exec_query_stats`, `sys.dm_exec_sql_text`и `sys.dm_exec_text_query_plan` и присвоить переменной `@xml_showplan` . Переменная `@xml_showplan` затем передается оператору `sp_create_plan_guide` в параметре `@hints` . Также можно создать структуру плана на основе плана запроса в кэше планов, используя хранимую процедуру [sp_create_plan_guide_from_handle](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md) .  
  
```  
USE AdventureWorks2012;  
GO  
SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;  
GO  
DECLARE @xml_showplan nvarchar(max);  
SET @xml_showplan = (SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%');  
  
EXEC sp_create_plan_guide   
    @name = N'Guide1_from_XML_showplan',   
    @stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = @xml_showplan;  
GO  
```  
  
  
