---
title: SET SHOWPLAN_XML (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 02/22/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SET SHOWPLAN_XML
- SET_SHOWPLAN_XML_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- statements [SQL Server], estimates
- SET SHOWPLAN_XML statement
- execution information and estimates [SQL Server]
- statements [SQL Server], information without processing
- XML [SQL Server], statement execution information
- SHOWPLAN_XML option
- estimated execution information [SQL Server]
ms.assetid: a467a1b3-10a5-43c4-9085-13d8aed549c9
caps.latest.revision: 48
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 9557a9576f214dcc84aa47e474797da9c570ff85
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38061632"
---
# <a name="set-showplanxml-transact-sql"></a>SET SHOWPLAN_XML (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Отключает выполнение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)]. Вместо этого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает подробные сведения о плане выполнения инструкций в виде верного XML-документа  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис
  
```  
  
SET SHOWPLAN_XML { ON | OFF }  
```  
  
## <a name="remarks"></a>Remarks  
 Значение SET SHOWPLAN_XML устанавливается во время запуска или выполнения, а не во время синтаксического анализа.  
  
 Если SET SHOWPLAN_XML имеет значение ON, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает данные плана выполнения для каждой инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], не выполняя ее. Когда параметру присвоено значение ON, возвращаются сведения по планам выполнения всех последующих инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)], пока параметру не будет снова присвоено значение OFF. Например, если инструкция CREATE TABLE будет выполнена при установленном в ON значении SET SHOWPLAN_XML, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вернет сообщение об ошибке в последующей инструкции SELECT, относящейся к той же таблице, сообщая пользователю, что указанной таблицы не существует. Следовательно, последующие ссылки на эту таблицу не действуют. Когда параметр SET SHOWPLAN_XML установлен в OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет инструкции, не создавая отчетов.  
  
 Параметр SET SHOWPLAN_XML предназначен для возвращения вывода с типом **nvarchar(max)** для таких приложений, как служебная программа **sqlcmd**, в которой вывод XML последовательно используется другими инструментами для отображения и обработки сведений о плане запроса.  
  
> [!NOTE]  
>  Динамическое административное представление **sys.dm_exec_query_plan** возвращает те же данные, что и инструкция SET SHOWPLAN XML, с типом данных **XML**. Эти данные возвращаются из столбца **query_plan** представления **sys.dm_exec_query_plan**. Дополнительные сведения см. в разделе [sys.dm_exec_query_plan (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md).  
  
 Инструкцию SET SHOWPLAN_XML нельзя вызывать внутри хранимых процедур. Она должна быть единственной инструкцией в пакете.  
  
 Инструкция SET STATISTICS XML возвращает данные в виде набора XML-документов. Каждый пакет после выполнения инструкции SET SHOWPLAN_XML ON сопровождается выводом одного документа. Каждый документ содержит текст инструкций, входящих в пакет, за которым следуют подробные сведения об этапах выполнения команды. Документ отображает оценку издержек выполнения, количество строк, индексов, к которым был произведен доступ, типы выполненных операторов, порядок соединения и другие данные о планах выполнения.  
  
 Документ, содержащий XML-схему для вывода в формате XML, формируемого инструкцией SET SHOWPLAN_XML, копируется во время установки в локальный каталог на компьютере, на котором установлен Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ее можно найти на диске, содержащем файлы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
 \Microsoft SQL Server\130\Tools\Binn\schemas\sqlserver\2004\07\showplan\showplanxml.xsd  
  
 Схему для инструкции SHOWPLAN также можно найти на [следующем веб-сайте](http://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409).  
  
> [!NOTE]  
>  Если в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] установлен параметр **Включить действительный план выполнения**, то при указании этого параметра SET вывод инструкции SHOWPLAN в формате XML формироваться не будет. Снимите флажок **Включить действительный план выполнения** перед использованием параметра SET.  
  
## <a name="permissions"></a>Разрешения  
 Для использования инструкции SET SHOWPLAN_XML требуются достаточные разрешения на выполнение инструкций, которые будут выполняться с после инструкции SET SHOWPLAN_XML, а также разрешение SHOWPLAN для всех баз данных, содержащих объекты, на которые ссылаются инструкции.  
  
 Чтобы инструкции SELECT, INSERT, UPDATE, DELETE, EXEC *stored_procedure* и EXEC *user_defined_function* создавали планы SHOWPLAN, пользователь должен:  
  
-   обладать необходимыми разрешениями на выполнение инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)];  
  
-   обладать разрешением SHOWPLAN для всех баз данных, содержащих объекты (такие как таблицы, представления и т. д.), на которые ссылаются инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Для всех остальных инструкций (например, DDL, USE *database_name*, SET, DECLARE, динамического SQL и т. д.) требуются лишь соответствующие разрешения на выполнение инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="examples"></a>Примеры  
 Две следующие инструкции используют параметры SET SHOWPLAN_XML, чтобы продемонстрировать, как происходят анализ и оптимизация использования индексов в запросах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 В предложении WHERE первого запроса оператор сравнения «равно» (=) применяется к индексированному столбцу. Во втором запросе в предложении WHERE используется оператор LIKE. Это заставляет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использовать поиск по кластеризованному индексу, чтобы найти удовлетворяющие условию в предложении WHERE данные. Значения атрибутов **EstimateRows** и **EstimatedTotalSubtreeCost** меньше у первого (индексируемого) запроса, из чего следует, что первый запрос был выполнен намного быстрее и потребовал меньше ресурсов, чем неиндексируемый запрос.  
  
```  
USE AdventureWorks2012;  
GO  
SET SHOWPLAN_XML ON;  
GO  
-- First query.  
SELECT BusinessEntityID   
FROM HumanResources.Employee  
WHERE NationalIDNumber = '509647174';  
GO  
-- Second query.  
SELECT BusinessEntityID, JobTitle  
FROM HumanResources.Employee  
WHERE JobTitle LIKE 'Production%';  
GO  
SET SHOWPLAN_XML OFF;  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
