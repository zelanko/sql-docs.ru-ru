---
title: Использование приложения SQL Server Profiler для создания и проверки структур плана | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- checking plan guides
- plan guides [SQL Server], testing
- plan guides [SQL Server], SQL Server Profiler
- matching queries to plan guides [SQL Server]
- testing plan guides
- SQL Server Profiler, plan guides
- plan guides [SQL Server], creating
- capturing query text [SQL Server]
- verifying plan guides
- Profiler [SQL Server Profiler], plan guides
- query-to-plan guide matching [SQL Server]
ms.assetid: 7018dbf0-1a1a-411a-88af-327bedf9cfbd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 543905343d74c9fbabe5f671d9021657ea5f76b5
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85066755"
---
# <a name="use-sql-server-profiler-to-create-and-test-plan-guides"></a>Использование приложения SQL Server Profiler для создания и проверки руководств планов
   При создании структуры плана приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] может применяться для извлечения точного текста запроса, который может использоваться в аргументе *statement_text* хранимой процедуры **sp_create_plan_guide**. Тем самым гарантируется, что во время компиляции структура плана будет соответствовать запросу. После создания структуры плана приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] может также использоваться для проверки того, что структура плана действительно соответствует запросу. Обычно проверка структуры плана приложением [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] нужна, чтобы убедиться в том, что запрос соответствует структуре плана.  
  
## <a name="capturing-query-text-by-using-sql-server-profiler"></a>Извлечение текста запроса при помощи приложения SQL Server Profiler  
 Если выполняется запрос и при помощи приложения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] извлекается текст точно в том виде, в котором он был представлен [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], можно создать структуру плана типа SQL или TEMPLATE, которое будет точно соответствовать тексту запроса. Благодаря этому структура плана может использоваться оптимизатором запросов.  
  
 Рассмотрим следующий запрос, представленный приложением в виде изолированного пакета:  
  
```  
SELECT COUNT(*) AS c  
FROM Sales.SalesOrderHeader AS h  
INNER JOIN Sales.SalesOrderDetail AS d  
  ON h.SalesOrderID = d.SalesOrderID  
WHERE h.OrderDate BETWEEN '20000101' and '20050101';  
```  
  
 Предположим, необходимо, чтобы запрос был выполнен при помощи операции соединения слиянием, но SHOWPLAN указывает на то, что запрос не использует соединение слиянием. Запрос нельзя изменить непосредственно в приложении, поэтому создается структура плана, определяющая, что указание запроса MERGE JOIN должно быть присоединено к запросу во время компиляции.  
  
 Для извлечения текста запроса точно в том виде, в каком его получает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выполните следующие шаги.  
  
1.  Запустите трассировку в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , выбрав тип события **SQL:BatchStarting** .  
  
2.  Позвольте приложению выполнить запрос.  
  
3.  Приостановите трассировку приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] .  
  
4.  Щелкните событие **SQL:BatchStarting** , соответствующее запросу.  
  
5.  Щелкните событие правой кнопкой мыши и выберите **Извлечь данные события**.  
  
    > [!IMPORTANT]  
    >  Не предпринимайте попыток скопировать текст пакета, выделяя его из нижней панели окна трассировки профайлера. Это может привести к несоответствию структуры плана исходному пакету.  
  
6.  Сохраните данные события в файле. Это и будет текст пакета.  
  
7.  Откройте в блокноте файл текста пакета и скопируйте текст в буфер копирования и вставки.  
  
8.  Создайте структуру плана и вставьте скопированный текст внутри кавычек (**''**), заданных для аргумента **@stmt** . Необходимо экранировать любые одинарные кавычки в **@stmt** аргументе, поставив перед ними еще одну одинарную кавычку. Следите за тем, чтобы при вставке одинарных кавычек не были вставлены или удалены другие символы. Например, литерал даты **'** 20000101 **'** должен быть указан в следующем формате: **''** 20000101 **''**.  
  
 Далее приводится структура плана:  
  
```  
EXEC sp_create_plan_guide   
    @name = N'MyGuide1',  
    @stmt = N'<paste the text copied from the batch text file here>',  
    @type = N'SQL',  
    @module_or_batch = NULL,  
    @params = NULL,  
    @hints = N'OPTION (MERGE JOIN)';  
```  
  
## <a name="testing-plan-guides-by-using-sql-server-profiler"></a>Проверка структур планов при помощи приложения SQL Server Profiler  
 Чтобы убедиться в том, что структура плана соответствует запросу, выполните следующие шаги.  
  
1.  Запустите трассировку в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , выбрав тип события **Showplan XML** (находится в узле **Производительность** ).  
  
2.  Позвольте приложению выполнить запрос.  
  
3.  Приостановите трассировку приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] .  
  
4.  Найдите событие **Showplan XML** для соответствующего запроса.  
  
    > [!NOTE]  
    >  Событие **XML-код инструкции Showplan компиляции запроса** использовать нельзя. **PlanGuideDB** не существует в этом событии.  
  
5.  Если структура плана имеет тип OBJECT или SQL, убедитесь, что событие **Showplan XML** содержит атрибуты **PlanGuideDB** и **PlanGuideName** для структуры плана, которая, как ожидается, соответствует запросу. Если структура плана имеет тип TEMPLATE, убедитесь, что событие **Showplan XML** содержит атрибуты **TemplatePlanGuideDB** и **TemplatePlanGuideName** для ожидаемой структуры плана. Тем самым производится проверка работы структуры плана. Эти атрибуты содержатся в **\<StmtSimple>** элементе плана.  
  
## <a name="see-also"></a>См. также:  
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)  
  
  
