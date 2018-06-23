---
title: Перенос планов запросов | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- query plans [SQL Server], migrating
- upgrading SQL Server, migrating query plans
- plan guides [SQL Server], migrating query plans
ms.assetid: 7e02a137-6867-4f6a-a45a-2b02674f7e65
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 66b481ab27af87a20f1a509cb10749c9f2ca1c15
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101588"
---
# <a name="migrate-query-plans"></a>Перенос планов запросов
  В большинстве случаев обновление базы данных до последней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приведет к повышению производительности запросов. Однако при наличии ответственных запросов, для которых производительность тщательно настроена, перед началом обновления может оказаться полезным сохранить планы запросов, создав для каждого из них структуру плана. Если после обновления оптимизатор запросов выбирает для некоторых запросов менее эффективный план, можно разрешить использование старых структур планов и заставить оптимизатор запросов пользоваться ими.  
  
 Чтобы создать структуру плана, перед началом обновления выполните следующие действия.  
  
1.  Запишите текущий план для каждого ответственного запроса с помощью [sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) хранимой процедуры и указанием плана запроса в подсказке запроса USE PLAN.  
  
2.  Убедитесь в том, что структура плана применена к запросу.  
  
3.  Обновите базу данных до более новой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Планы сохранятся в структурах плана обновленной базы данных и понадобятся в том случае, если потребуется регрессия планов после обновления.  
  
     Рекомендуется не включать структуры планов после обновления, это может позволить упустить возможность применения в новой версии более оптимальных планов или полезных перекомпиляций в соответствии с обновленной статистикой.  
  
4.  Если после обновления выбираются менее эффективные планы, включите все или некоторые из структур планов, заменив ими новые.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует запись старого плана для запроса путем создания структуры плана.  
  
### <a name="step-1-collect-the-plan"></a>Шаг 1: Получите план  
 План запроса, записываемый в структуру плана, должен иметь формат XML. Планы запросов в формате XML могут быть созданы следующими способами.  
  
-   [SET SHOWPLAN_XML](/sql/t-sql/statements/set-showplan-xml-transact-sql)  
  
-   [SET STATISTICS XML](/sql/t-sql/statements/set-statistics-xml-transact-sql)  
  
-   Запрос столбцу query_plan [sys.dm_exec_query_plan](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql) функции динамического управления.  
  
-   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] [Showplan XML](../../relational-databases/event-classes/showplan-xml-event-class.md), [Showplan XML Statistics Profile](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md), и [Showplan XML For Query Compile](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md) классов событий.  
  
 Следующий пример собирает план запроса для инструкции `SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;` путем запроса динамических административных представлений.  
  
```  
USE AdventureWorks;  
GO  
SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%';  
GO  
```  
  
### <a name="step-2-create-the-plan-guide-to-force-the-plan"></a>Шаг 2: Создание структуры плана, чтобы принудительно выбрать план  
 Скопируйте план запроса в формате XML, полученный любым из описанных выше способов, из структуры плана, а затем вставьте его в виде строкового литерала в указание запроса USE PLAN предложения OPTION процедуры sp_create_plan_guide.  
  
 В самом XML-плане перед созданием структуры плана необходимо экранировать входящие в него кавычки ('). Например, план, содержащий `WHERE A.varchar = 'This is a string'`, должен быть изменен и содержать `WHERE A.varchar = ''This is a string''`.  
  
 В следующем примере создается структура плана для плана запроса, собранного на шаге 1, и в параметр `@hints` вставляется XML Showplan для запроса. Для краткости в пример включена только часть выходных данных Showplan.  
  
```  
EXECUTE sp_create_plan_guide   
@name = N'Guide1',  
@stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',  
@type = N'SQL',  
@module_or_batch = NULL,  
@params = NULL,  
@hints = N'OPTION(USE PLAN N''<ShowPlanXML xmlns=''''http://schemas.microsoft.com/sqlserver/2004/07/showplan''''   
    Version=''''0.5'''' Build=''''9.00.1116''''>  
    <BatchSequence><Batch><Statements><StmtSimple>  
    …  
    </StmtSimple></Statements></Batch>  
    </BatchSequence></ShowPlanXML>'')';  
GO  
```  
  
### <a name="step-3-verify-that-the-plan-guide-is-applied-to-the-query"></a>Шаг 3: Убедитесь, что структура плана применена к запросу  
 Выполните запрос еще раз и проверьте созданный план запроса. Убедитесь, что план выполнения совпадает с тем, что был указан в структуре плана.  
  
## <a name="see-also"></a>См. также  
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Указания запросов (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query)   
 [Руководства планов](../../relational-databases/performance/plan-guides.md)  
  
  
