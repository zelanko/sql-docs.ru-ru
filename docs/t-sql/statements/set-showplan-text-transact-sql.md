---
title: "Инструкция SET SHOWPLAN_TEXT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHOWPLAN_TEXT
- SET_SHOWPLAN_TEXT_TSQL
- SET SHOWPLAN_TEXT
- SHOWPLAN_TEXT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- statements [SQL Server], estimates
- execution information and estimates [SQL Server]
- statements [SQL Server], information without processing
- SET SHOWPLAN_TEXT statement
- canceling statement execution
- SHOWPLAN_TEXT option
- stopping statement execution
- estimated execution information [SQL Server]
ms.assetid: 2c4f3fc8-ff2c-4790-8b74-e7e8ef58f9a6
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7abd42acdcbfa4274686d3d8162e727cf36e5ee7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-showplantext-transact-sql"></a>SET SHOWPLAN_TEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Приводит к тому, что Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не выполняет инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)]. Вместо этого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает подробные сведения о ходе выполнения инструкций.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET SHOWPLAN_TEXT { ON | OFF }  
```  
  
## <a name="remarks"></a>Замечания  
 Установка значения параметра SET SHOWPLAN_TEXT выполняется во время выполнения или запуска, а не во время синтаксического анализа.  
  
 Если выполнена инструкция SET SHOWPLAN_TEXT ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает сведения для каждой инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], не выполняя ее. Когда параметру присвоено значение ON, возвращаются сведения по планам выполнения всех последующих инструкций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], пока параметру не будет снова присвоено значение OFF. Например, если инструкция CREATE TABLE будет выполнена при выполненной инструкции SET SHOWPLAN_TEXT ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вернет сообщение об ошибке в последующей инструкции SELECT, относящейся к той же таблице, сообщая пользователю, что указанная таблица не существует. Следовательно, последующие ссылки на эту таблицу не действуют. Если выполнена инструкция SET SHOWPLAN_TEXT OFF, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет инструкции, не создавая отчет с информацией по плану выполнения.  
  
 Инструкция SET SHOWPLAN_TEXT предназначена для возврата доступного для чтения вывода для приложений командной строки Microsoft Win32, таких как **osql** программы. Инструкция SET SHOWPLAN_ALL возвращает более подробные данные, предназначенные для обработки программами, специально ориентированными на этот формат вывода.  
  
 Инструкции SET SHOWPLAN_TEXT и SET SHOWPLAN_ALL нельзя указывать в хранимой процедуре. Их можно указывать только как инструкции в пакете.  
  
 Инструкция SET SHOWPLAN_TEXT возвращает данные в виде набора строк, формирующего иерархическое дерево, которое представляет последовательность шагов, выполняемых обработчиком запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по ходу выполнения каждой инструкции. Каждой инструкции, отраженной в выходных данных, соответствует одна строка с текстом инструкции, за которой следуют несколько строк с подробными описаниями шагов выполнения. Следующая таблица содержит описание столбцов вывода.  
  
|Имя столбца|Description|  
|-----------------|-----------------|  
|**StmtText**|Для строк, имеющих отличный от PLAN_ROW тип, этот столбец содержит текст инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. В строках типа PLAN_ROW этот столбец содержит описание операции. Этот столбец содержит физический оператор и может также, при необходимости, содержать логический оператор. За этим столбцом также может следовать описание, определяемое физическим оператором. Дополнительные сведения о физических операторах см. в разделе **аргумент** столбца в [SET SHOWPLAN_ALL &#40; Transact-SQL &#41; ](../../t-sql/statements/set-showplan-all-transact-sql.md).|  
  
 Дополнительные сведения о физических и логических операторах, отображаемых в выводе инструкции Showplan см. в разделе [Showplan логических и физических Справочник по операторам](../../relational-databases/showplan-logical-and-physical-operators-reference.md)  
  
## <a name="permissions"></a>Permissions  
 Для использования инструкции SET SHOWPLAN_TEXT требуются достаточные разрешения на выполнение инструкций, которые будут выполняться с инструкцией SET SHOWPLAN_TEXT, а также разрешение SHOWPLAN для всех баз данных, содержащих объекты, на которые ссылаются инструкции.  
  
 Для SELECT, INSERT, UPDATE, DELETE, EXEC *stored_procedure*и EXEC *user_defined_function* инструкции для получения инструкции Showplan, пользователь должен:  
  
-   обладать необходимыми разрешениями на выполнение инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)];  
  
-   Обладать разрешениями SHOWPLAN для всех баз данных, содержащих объекты (например таблицы, представления и т. д.), на которые ссылаются инструкции Transact-SQL.  
  
 Для всех остальных инструкций, например DDL, USE *имя_базы_данных*, SET, DECLARE, динамического SQL и так далее, соответствующие разрешения на выполнение [!INCLUDE[tsql](../../includes/tsql-md.md)] операторы нужны.  
  
## <a name="examples"></a>Примеры  
 Этот пример демонстрирует использование индексов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при обработке инструкций.  
  
 Запрос, использующий индекс:  
  
```  
USE AdventureWorks2012;  
GO  
SET SHOWPLAN_TEXT ON;  
GO  
SELECT *  
FROM Production.Product   
WHERE ProductID = 905;  
GO  
SET SHOWPLAN_TEXT OFF;  
GO  
```  
  
 Результирующий набор:  
  
```  
StmtText                                             
---------------------------------------------------  
SELECT *  
FROM Production.Product   
WHERE ProductID = 905;   
  
StmtText                                                                                                                                                                                        
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------  
|--Clustered Index Seek(OBJECT:([AdventureWorks2012].[Production].[Product].[PK_Product_ProductID]), SEEK:([AdventureWorks2012].[Production].[Product].[ProductID]=CONVERT_IMPLICIT(int,[@1],0)) ORDERED FORWARD)   
```  
  
 Запрос, не использующий индекс:  
  
```  
USE AdventureWorks2012;  
GO  
SET SHOWPLAN_TEXT ON;  
GO  
SELECT *  
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;  
GO  
SET SHOWPLAN_TEXT OFF;  
GO  
```  
  
 Результирующий набор:  
  
```  
StmtText                                                                  
------------------------------------------------------------------------  
SELECT *  
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;   
  
StmtText                                                                                                                                                                                                  
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------  
|--Clustered Index Scan(OBJECT:([AdventureWorks2012].[Production].[ProductCostHistory].[PK_ProductCostHistory_ProductCostID]), WHERE:([AdventureWorks2012].[Production].[ProductCostHistory].[StandardCost]<[@1]))  
```  
  
## <a name="see-also"></a>См. также:  
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET SHOWPLAN_ALL &#40; Transact-SQL &#41;](../../t-sql/statements/set-showplan-all-transact-sql.md)  
  
  

