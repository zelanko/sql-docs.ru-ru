---
title: Перекомпиляция хранимой процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 10/28/2019
ms.prod: sql
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- sp_recompile
- WITH RECOMPILE clause
- recompiling stored procedures
- stored procedures [SQL Server], recompiling
ms.assetid: b90deb27-0099-4fe7-ba60-726af78f7c18
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: df92be946b13a4643f6ddca870ea98ff64b3d9d9
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86002746"
---
# <a name="recompile-a-stored-procedure"></a>Перекомпиляция хранимой процедуры
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  В этом разделе описывается, как перекомпилировать хранимую процедуру в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]. Это можно сделать тремя способами: указать параметр **WITH RECOMPILE** в определении процедуры или при вызове процедуры, задать указание запроса **RECOMPILE** в отдельных инструкциях или использовать системную хранимую процедуру **sp_recompile** . В этом разделе описывается использование параметра WITH RECOMPILE при создании определения процедуры и выполнении существующей процедуры. Также описывается использование системной хранимой процедуры sp_recompile для перекомпиляции существующей процедуры.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Для перекомпиляции хранимой процедуры используется:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
  
-   Когда процедура компилируется впервые или повторно, выполняется оптимизация плана запроса процедуры для текущего состояния базы данных и ее объектов. Если данные или структура базы данных подвергаются значительным изменениям, то при перекомпиляции процедуры ее план запроса обновляется и оптимизируется в соответствии с этими изменениями. Это может повысить производительность обработки процедуры.  
  
-   Иногда необходимо принудительно выполнить перекомпиляцию процедуры, а иногда это выполняется автоматически. Автоматическая перекомпиляция выполняется при каждом перезапуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Она также проводится, если в базовой таблице, на которую ссылается процедура, происходят изменения физической структуры.  
  
-   Другая причина для принудительного перекомпилирования процедуры — это нейтрализация пробного сохранения параметров при компиляции процедуры. Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет процедуры, значения всех используемых при компиляции параметров включаются в формируемый план запроса. Если эти значения типичны для последующих вызовов процедуры, то компиляция и выполнение хранимой процедуры с этим планом запроса происходит быстрее. Если значения параметров для процедуры часто оказываются нетипичными, то принудительная перекомпиляция процедуры и создание нового плана на основе других значений параметров может повысить производительность.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обладает возможностью перекомпиляции процедур на уровне инструкций. Во время перекомпиляции хранимой процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] заново компилирует только вызвавшую этот процесс инструкцию, а не всю процедуру.  
  
-   Если некоторые запросы в процедуре регулярно используют нетипичные или временные значения, то можно повысить производительность процедуры, используя указание запроса RECOMPILE в таких запросах. Поскольку перекомпиляцию будут проходить только запросы, использующие это указание, а не вся процедура, то повторная компиляция [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]будет работать на уровне инструкций. Однако, помимо использования текущих значений параметров процедуры, указание запроса RECOMPILE при компиляции инструкции также использует значения локальных переменных в хранимой процедуре. Дополнительные сведения см. в разделе [Указания запросов (Transact-SQL)](../../t-sql/queries/hints-transact-sql-query.md).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Параметр**WITH RECOMPILE**  
 Если этот параметр используется при создании определения процедуры, то необходимо разрешение CREATE PROCEDURE в базе данных и разрешение ALTER на схему, в которой создается процедура.  
  
 Если этот параметр используется в инструкции EXECUTE, требуются разрешения EXECUTE на процедуру. Разрешения на саму инструкцию EXECUTE не требуются, однако требуются разрешения на выполнение процедуры, упоминаемой в инструкции EXECUTE. Дополнительные сведения см. в разделе [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md).  
  
 Указание запроса **RECOMPILE**  
 Эта возможность используется при создании процедуры, и указание включается в инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] в процедуре. Таким образом, требуется разрешение CREATE PROCEDURE в базе данных и разрешение ALTER на схему, в которой создается процедура.  
  
 Выполнение системной хранимой процедуры**sp_recompile**  
 Необходимо разрешение ALTER на указанную процедуру.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  

1. Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
1. На панели «Стандартная» нажмите **Создать запрос**.  
  
1. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере создается определение процедуры.  

   ```sql
   USE AdventureWorks2012;  
   GO  
   IF OBJECT_ID ( 'dbo.uspProductByVendor', 'P' ) IS NOT NULL   
       DROP PROCEDURE dbo.uspProductByVendor;  
   GO  
   CREATE PROCEDURE dbo.uspProductByVendor @Name varchar(30) = '%'  
   WITH RECOMPILE  
   AS  
       SET NOCOUNT ON;  
       SELECT v.Name AS 'Vendor name', p.Name AS 'Product name'  
       FROM Purchasing.Vendor AS v   
       JOIN Purchasing.ProductVendor AS pv   
         ON v.BusinessEntityID = pv.BusinessEntityID   
       JOIN Production.Product AS p   
         ON pv.ProductID = p.ProductID  
       WHERE v.Name LIKE @Name;  
   ```  
  
### <a name="to-recompile-a-stored-procedure-by-using-the-with-recompile-option"></a>Перекомпиляция хранимой процедуры с использованием параметра WITH RECOMPILE   
  
Выберите **Создать запрос**, скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. Процедура будет выполнена с повторной компиляцией плана запроса.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXECUTE HumanResources.uspProductByVendor WITH RECOMPILE;  
GO
```  
  
### <a name="to-recompile-a-stored-procedure-by-using-sp_recompile"></a>Перекомпиляция хранимой процедуры с использованием процедуры sp_recompile  

Выберите **Создать запрос**, скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. Процедура не будет выполнена, но будет помечена для повторной компиляции, и при следующем выполнении процедуры ее план запроса будет обновлен.  

```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_recompile N'dbo.uspProductByVendor';   
GO
```  
  
## <a name="see-also"></a>См. также:  
 [Создание хранимой процедуры](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [Изменение хранимой процедуры](../../relational-databases/stored-procedures/modify-a-stored-procedure.md)   
 [Изменение имени хранимой процедуры](../../relational-databases/stored-procedures/rename-a-stored-procedure.md)   
 [Просмотр определения хранимой процедуры](../../relational-databases/stored-procedures/view-the-definition-of-a-stored-procedure.md)   
 [Просмотр зависимостей хранимой процедуры](../../relational-databases/stored-procedures/view-the-dependencies-of-a-stored-procedure.md)   
 [DROP PROCEDURE (Transact-SQL)](../../t-sql/statements/drop-procedure-transact-sql.md)  
  
  
