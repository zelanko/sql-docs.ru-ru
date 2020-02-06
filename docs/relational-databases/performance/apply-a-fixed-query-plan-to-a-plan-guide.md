---
title: Применение фиксированного плана запроса к структуре плана | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: bbf401f9-af7c-48e7-8a43-bf25e8af2fd7
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 8bb64d5a74fbc7b72c543a49fcf658caea6a2ef4
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67985068"
---
# <a name="apply-a-fixed-query-plan-to-a-plan-guide"></a>Применение фиксированного плана запроса к структуре плана
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Можно применить фиксированный план запроса к руководству плана типов OBJECT или SQL. Структуры планов, применяющие фиксированные планы запроса, удобно использовать в тех случаях, когда известно, что есть план выполнения, который работает с большей производительностью, чем выбранный оптимизатором для конкретного запроса.  
  
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
  
  
