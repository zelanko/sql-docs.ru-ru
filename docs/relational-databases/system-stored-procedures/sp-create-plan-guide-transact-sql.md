---
description: sp_create_plan_guide (Transact-SQL)
title: sp_create_plan_guide (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_create_plan_guide
- sp_create_plan_guide_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_create_plan_guide
ms.assetid: 5a8c8040-4f96-4c74-93ab-15bdefd132f0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0e7cc07a0878eefdb6f8c0cdf33cf6e063651afb
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89539067"
---
# <a name="sp_create_plan_guide-transact-sql"></a>sp_create_plan_guide (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Создает структуру плана для связывания указаний запроса или фактических планов запросов с запросами в базе данных. Дополнительные сведения о структурах планов см. в разделе [Руководства планов](../../relational-databases/performance/plan-guides.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_create_plan_guide [ @name = ] N'plan_guide_name'  
    , [ @stmt = ] N'statement_text'  
    , [ @type = ] N'{ OBJECT | SQL | TEMPLATE }'  
    , [ @module_or_batch = ]  
      {   
                    N'[ schema_name. ] object_name'  
        | N'batch_text'  
        | NULL  
      }  
    , [ @params = ] { N'@parameter_name data_type [ ,...n ]' | NULL }   
    , [ @hints = ] { N'OPTION ( query_hint [ ,...n ] )'   
                 | N'XML_showplan'  
                 | NULL }  
```  
  
## <a name="arguments"></a>Аргументы  
 [ \@ name =] N '*plan_guide_name*'  
 Имя структуры плана. Имена структур планов ограничены областью текущей базы данных. *plan_guide_name* должны соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md) и не может начинаться со знака решетки (#). Максимальная длина *plan_guide_name* — 124 символов.  
  
 [ \@ stmt =] N '*statement_text*'  
 Инструкция языка [!INCLUDE[tsql](../../includes/tsql-md.md)], для которой создается структура плана. Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оптимизатор запросов распознает запрос, соответствующий *statement_text*, *plan_guide_name* вступает в силу. Для успешности создания структуры плана *statement_text* должны присутствовать в контексте, заданном \@ параметрами Type, \@ module_or_batch и \@ params.  
  
 *statement_text* должны быть предоставлены способом, который позволяет оптимизатору запросов сопоставлять его с соответствующей инструкцией, указанной в пакете или модуле, идентифицируемом \@ module_or_batch и \@ params. Дополнительные сведения см. в разделе "Замечания". Размер *statement_text* ограничивается только объемом доступной памяти сервера.  
  
 [ \@ Type =] N ' {Object | SQL | ШАБЛОН} "  
 Тип сущности, в которой отображается *statement_text* . Указывает контекст для сопоставления *statement_text* *plan_guide_name*.  
  
 OBJECT  
 Указывает, *statement_text* отображается в контексте [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимой процедуры, скалярной функции, функции с табличным значением из множественных инструкций или [!INCLUDE[tsql](../../includes/tsql-md.md)] триггера DML в текущей базе данных.  
  
 SQL  
 Указывает, *statement_text* появляется в контексте изолированной инструкции или пакета, который может быть передан [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] любым механизмом. [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции, отправленные объектами среды CLR или расширенными хранимыми процедурами или с помощью EXEC N '*sql_string*', обрабатываются на сервере как пакеты и, следовательно, должны быть идентифицированы как \@ тип **=** "SQL". Если задано значение SQL, то указание запроса с ПАРАМЕТРом {FORCED | SIMPLE} нельзя указывать в \@ параметре указания.  
  
 TEMPLATE  
 Указывает, что структура плана применяется к любому запросу, который параметризуются в форму, указанную в *statement_text*. Если указан шаблон, только параметризация {FORCED | В параметре hints можно указать указание запроса SIMPLE} \@ . Дополнительные сведения о структурах планов шаблонов см. в разделе [Определение поведения параметризации запросов с помощью структур планов](../../relational-databases/performance/specify-query-parameterization-behavior-by-using-plan-guides.md).  
  
 [ \@ module_or_batch =] {N ' [ *schema_name*. ] *object_name*"| N '*batch_text*' | ЗАКАНЧИВАЮЩ  
 Указывает либо имя объекта, в котором отображается *statement_text* , либо текст пакета, в котором отображается *statement_text* . Текст пакета не может включать инструкцию USE*Database* .  
  
 Чтобы структура плана соответствовала пакету, отправленному из приложения, *batch_tex*t должен быть указан в том же формате, что и символьный символ, в том виде, в каком он передан [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для упрощения соответствия формата внутренние преобразования не выполняются. Дополнительные сведения см. в разделе "Примечания".  
  
 [*schema_name*.] *object_name* указывает имя [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимой процедуры, скалярной функции, функции с табличным значением из множественных инструкций или [!INCLUDE[tsql](../../includes/tsql-md.md)] триггера DML, содержащего *statement_text*. Если *schema_name* не указан, *schema_name* использует схему текущего пользователя. Если указано значение NULL и \@ Type = "SQL", то для параметра \@ module_or_batch задается значение \@ stmt. Если \@ Type = ' template **\'** , \@ module_or_batch должны иметь значение null.  
  
 [ \@ params =] {N '* \@ parameter_name data_type* [,*... n* ] ' | ЗАКАНЧИВАЮЩ  
 Задает определения всех параметров, внедренных в *statement_text*. \@параметры применяются только в том случае, если выполняется одно из следующих условий.  
  
-   \@Введите = "SQL" или "TEMPLATE". Если параметр "TEMPLATE", \@ params не должен иметь значение null.  
  
-   *statement_text* передается с помощью sp_executesql, а значение \@ параметра params указывается или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутренне отправляет инструкцию после его параметризации. Отправка параметризованных запросов через API-интерфейсы базы данных (включая ODBC, OLE DB и ADO.NET) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выглядит как вызов процедуры sp_executesql либо API-процедуры серверного курсора, поэтому они также могут совпадать со структурой плана SQL или TEMPLATE.  
  
 * \@ parameter_name data_type* должны быть предоставлены в том же формате, в котором они передаются с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] помощью sp_executesql или отправляются внутренне после параметризации. Дополнительные сведения см. в разделе "Примечания". Если пакет не содержит параметров, необходимо указать значение NULL. Размер \@ параметров ограничен только доступной памятью сервера.  
  
 [ \@ hints =] {N'OPTION (*query_hint* [,*... n* ]) "| N '*XML_showplan*' | ЗАКАНЧИВАЮЩ  
 N'OPTION (*query_hint* [,*... n* ])  
 Указывает предложение OPTION для присоединения к запросу, совпадающему с \@ stmt. \@ указания должны быть синтаксически такими же, как и предложение OPTION в инструкции SELECT, и могут содержать любую допустимую последовательность указания запроса.  
  
 N "*XML_showplan*"  
 План запроса в формате XML для применения в качестве указания.  
  
 Значение аргумента XML_showplan рекомендуется присвоить переменной, иначе каждый символ одиночной кавычки необходимо предварять дополнительным символом одиночной кавычки. См. пример Д.  
  
 NULL  
 Указывает, что любое существующее указание, заданное в предложении OPTION запроса, не применяется к запросу. Дополнительные сведения см. в разделе [предложение OPTION &#40;&#41;Transact-SQL ](../../t-sql/queries/option-clause-transact-sql.md).  
  
## <a name="remarks"></a>Примечания  
 Аргументы процедуры sp_create_plan_guide должны задаваться в указанном порядке. При задании значений параметрам процедуры **sp_create_plan_guide**все имена параметров необходимо указывать явно или вообще не указывать. Например, если указано ** \@ Name =** , то необходимо также указать ** \@ stmt =** , ** \@ Type =** и т. д. Аналогично, если ** \@ имя =** опущено и указано только значение параметра, остальные имена параметров также необходимо опустить и указать только их значения. Имена аргументов приводятся исключительно в целях описания, чтобы помочь разобраться с синтаксисом. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не проверяет соответствие указанных имен параметров их позициям.  
  
 Можно создать несколько структур планов OBJECT или SQL для одного и того же запроса и пакета либо модуля. Однако только одна структура плана может быть включена в данный момент времени.  
  
 Структуры планов типа OBJECT не могут быть созданы для \@ module_or_batch значения, ссылающегося на хранимую процедуру, функцию или триггер DML, который указывает предложение WITH ENCRYPTION или является временным.  
  
 Попытка удаления или изменения функции, хранимой процедуры или триггера DML, на которые имеется ссылка в структуре плана (как включенных, так и отключенных), приводит к ошибке. Попытка удалить таблицу, для которой определен триггер, имеющий соответствующую ссылку в структуре плана, также вызывает ошибку.  
  
> [!NOTE]
> Структуру планов можно использовать не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md). Структуры планов видны в любом выпуске. Можно также присоединить базу данных, содержащую структуры планов, к любой версии. Структуры планов остаются нетронутыми при восстановлении или присоединении базы данных к обновленной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Следует тщательно взвешивать необходимость использования структур планов в каждой базе данных после выполнения обновления сервера.  
  
## <a name="plan-guide-matching-requirements"></a>Требования к соответствию структуры плана  
 Для структур планов, которые указывают \@ Type = "SQL" или \@ Type = "Template", чтобы успешно сопоставить запрос, значения для *batch_text* и * \@ parameter_name data_type* [,*... n* ] должен быть указан точно в том же формате, что и их аналоги, отправленные приложением. Это означает, что необходимо предоставить текст пакета в точном соответствии с текстом, получаемым компилятором [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для захвата действительного текста пакета и параметра используется приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Дополнительные сведения см. [в разделе использование SQL Server Profiler для создания и тестирования структур планов](../../relational-databases/performance/use-sql-server-profiler-to-create-and-test-plan-guides.md).  
  
 Если \@ Type = "SQL" и \@ module_or_batch имеет значение null, для параметра \@ module_or_batch задается значение \@ stmt. Это означает, что значение для *statement_text* должно быть указано в том же формате, что и символ, в том виде, в каком он передан [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для упрощения соответствия формата внутренние преобразования не выполняются.  
  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соответствует значению *statement_text* для *batch_text* и * \@ parameter_name data_type* [,*... n* ] или, если \@ Type = **\'** Object ", к тексту соответствующего запроса внутри *object_name*следующие строковые элементы не рассматриваются:  
  
-   Пробельные символы (знаки табуляции, пробелы, возвраты каретки и переводы строки) внутри строки.  
  
-   Комментарии ( **--** или **/\*   \*/** ).  
  
-   Точка с запятой (;) в конце строки.  
  
 Например, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может сопоставлять строку *statement_text* со `N'SELECT * FROM T WHERE a = 10'` следующим *batch_text*:  
  
 ```
 N'SELECT *
 FROM T
 WHERE a = 10' 
 ```
 
 Однако одна и та же строка не будет соответствовать этому *batch_text*:  
  
 `N'SELECT * FROM T WHERE b = 10'`  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пропускает знаки возврата каретки, перевода строки и пробелы внутри первого запроса. При рассмотрении второго запроса строки `WHERE b = 10` и `WHERE a = 10` считаются различными. Результат сравнения учитывает регистр и наличие диакритических знаков (даже в случае, когда в параметрах сортировки базы данных задана сортировка без учета регистра), за исключением тех случаев, когда используются ключевые слова, игнорирующие регистр. Сравнение выполняется без учета сокращенных форм ключевых слов. Например, ключевые слова `EXECUTE`, `EXEC` и `execute` являются эквивалентными.  
  
## <a name="plan-guide-effect-on-the-plan-cache"></a>Воздействие структуры плана на кэш планов  
 Создание структуры плана в модуле стирает план запроса для этого модуля из кэша планов. Создание структуры плана типа OBJECT или SQL в потоке стирает план запроса для потока, который имеет такое же значение хеш-функции. Создание структуры плана типа TEMPLATE стирает все потоки с одним оператором из кэша планов через базу данных.  
  
## <a name="permissions"></a>Разрешения  
 Для создания структуры плана типа OBJECT требуется `ALTER` разрешение на упоминаемый объект. Чтобы создать структуру плана типа SQL или TEMPLATE, требуется `ALTER` разрешение в текущей базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-plan-guide-of-type-object-for-a-query-in-a-stored-procedure"></a>A. Создание структуры плана типа OBJECT для запроса в хранимой процедуре  
 В приведенном ниже примере создается структура плана, с которой сопоставляется запрос, выполняемый в контексте хранимой процедуры приложения, а также происходит применение к запросу указания `OPTIMIZE FOR`.  
  
 Ниже приведена хранимая процедура.  
  
```sql  
IF OBJECT_ID(N'Sales.GetSalesOrderByCountry', N'P') IS NOT NULL  
    DROP PROCEDURE Sales.GetSalesOrderByCountry;  
GO  
CREATE PROCEDURE Sales.GetSalesOrderByCountry   
    (@Country_region nvarchar(60))  
AS  
BEGIN  
    SELECT *  
    FROM Sales.SalesOrderHeader AS h   
    INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
    INNER JOIN Sales.SalesTerritory AS t   
        ON c.TerritoryID = t.TerritoryID  
    WHERE t.CountryRegionCode = @Country_region;  
END  
GO  
```  
  
 Ниже представлена структура плана, созданная по запросу в хранимой процедуре.  
  
```sql  
EXEC sp_create_plan_guide   
    @name =  N'Guide1',  
    @stmt = N'SELECT *  
              FROM Sales.SalesOrderHeader AS h   
              INNER JOIN Sales.Customer AS c   
                 ON h.CustomerID = c.CustomerID  
              INNER JOIN Sales.SalesTerritory AS t   
                 ON c.TerritoryID = t.TerritoryID  
              WHERE t.CountryRegionCode = @Country_region',  
    @type = N'OBJECT',  
    @module_or_batch = N'Sales.GetSalesOrderByCountry',  
    @params = NULL,  
    @hints = N'OPTION (OPTIMIZE FOR (@Country_region = N''US''))';  
```  
  
### <a name="b-creating-a-plan-guide-of-type-sql-for-a-stand-alone-query"></a>Б. Создание структуры плана типа SQL для изолированного запроса  
 В приведенном ниже примере создается структура плана, с которой сопоставляется запрос из пакета, переданного приложением, использующим системную хранимую процедуру sp_executesql.  
  
 Ниже представлен пакет.  
  
```sql  
SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC;  
```  
  
 Для предотвращения создания по данному запросу параллельного плана выполнения необходимо создать следующую структуру плана.  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'Guide1',   
    @stmt = N'SELECT TOP 1 *   
              FROM Sales.SalesOrderHeader   
              ORDER BY OrderDate DESC',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (MAXDOP 1)';  
```  
  
### <a name="c-creating-a-plan-guide-of-type-template-for-the-parameterized-form-of-a-query"></a>В. Создание структуры плана типа TEMPLATE для параметризованного запроса  
 В приведенном ниже примере создается структура плана, которой сопоставляется запрос заданной параметризованной формы и которое вынуждает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметризовать поступающие запросы. Два приведенных ниже запроса являются синтаксическими эквивалентами, однако различаются своими значениями постоянных литералов.  
  
```sql  
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
  
```sql  
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
  
```sql  
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
>  Значения постоянных литералов аргумента `@stmt`, передаваемого в процедуру sp_get_query_template, определяют тип данных для аргумента, заменяющего указанные литералы. Это влияет на совпадение структур планов. Возможно, придется создать несколько структур плана для обработки различных диапазонов значений аргумента.  
  
### <a name="d-creating-a-plan-guide-on-a-query-submitted-by-using-an-api-cursor-request"></a>Г. Создание структуры плана на основе запроса, переданного с помощью запроса курсора API  
 Структуры планов могут совпадать с запросами, передаваемыми с помощью процедур серверных курсоров API. К указанным процедурам относятся sp_cursorprepare, sp_cursorprepexec и sp_cursoropen. Приложения, использующие API-интерфейсы ADO, OLE DB и ODBC, часто связываются с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи серверных курсоров API. Вызов процедур серверного курсора API-интерфейса можно увидеть в трассировках приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], просматривая событие трассировки SQL Profiler RPC:Starting.  
  
 Допустим, что для запроса, настраиваемого с помощью структуры плана, в событии трассировки RPC:Starting приложения SQL Profiler имеются следующие данные.  
  
```sql  
DECLARE @p1 int;  
SET @p1=-1;  
DECLARE @p2 int;  
SET @p2=0;  
DECLARE @p5 int;  
SET @p5=4104;  
DECLARE @p6 int;  
SET @p6=8193;  
DECLARE @p7 int;  
SET @p7=0;  
EXEC sp_cursorprepexec @p1 output,@p2 output,N'@P1 varchar(255),@P2 varchar(255)',N'SELECT * FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID WHERE h.OrderDate BETWEEN @P1 AND @P2',@p5 OUTPUT,@p6 OUTPUT,@p7 OUTPUT,'20040101','20050101'  
SELECT @p1, @p2, @p5, @p6, @p7;  
```  
  
 Пусть необходимо изменить следующую настройку запроса `SELECT` вызова процедуры `sp_cursorprepexec`: используемое соединение слиянием необходимо заменить хэш-соединением. Запрос, передаваемый с помощью процедуры `sp_cursorprepexec`, является параметризованным, включая строку запроса и строку параметров. В точности копируя строки запроса и параметров вызова процедуры `sp_cursorprepexec`, можно создать следующую структуру плана.  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'APICursorGuide',  
    @stmt = N'SELECT * FROM Sales.SalesOrderHeader AS h   
              INNER JOIN Sales.SalesOrderDetail AS d   
                ON h.SalesOrderID = d.SalesOrderID   
              WHERE h.OrderDate BETWEEN @P1 AND @P2',  
    @type = N'SQL',  
    @module_or_batch = NULL,  
    @params = N'@P1 varchar(255),@P2 varchar(255)',  
    @hints = N'OPTION(HASH JOIN)';  
```  
  
 При последующем выполнении приложением данный запрос будет соответствовать структуре плана, и для обработки запроса будет использоваться хэш-соединение.  
  
### <a name="e-creating-a-plan-guide-by-obtaining-the-xml-showplan-from-a-cached-plan"></a>Д. Создание структуры плана с помощью получения данных XML Showplan из плана в кэш-памяти  
 В следующем примере создается структура плана для простой нерегламентированной инструкции SQL. Требуемый план запроса для этого оператора представлен в структуре плана путем указания XML Showplan для запроса непосредственно в параметре `@hints` . В примере сначала выполняется инструкция SQL для создания плана в кэше планов. В этом примере допустим, что созданный план является желаемым планом и не требуется дополнительной настройки запросов. Данные XML Showplan для запроса необходимо получить с помощью запроса к динамическим административным представлениям `sys.dm_exec_query_stats`, `sys.dm_exec_sql_text`и `sys.dm_exec_text_query_plan` и присвоить переменной `@xml_showplan` . Переменная `@xml_showplan` затем передается оператору `sp_create_plan_guide` в параметре `@hints` . Также можно создать структуру плана на основе плана запроса в кэше планов, используя хранимую процедуру [sp_create_plan_guide_from_handle](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md) .  
  
```sql  
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
    @hints =@xml_showplan;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Структуры планов](../../relational-databases/performance/plan-guides.md)   
 [sp_control_plan_guide (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql.md)   
 [sys.plan_guides (Transact-SQL)](../../relational-databases/system-catalog-views/sys-plan-guides-transact-sql.md)   
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys. dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_cached_plans (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)   
 [sys. dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)   
 [sys.fn_validate_plan_guide (Transact-SQL)](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md)   
 [sp_get_query_template &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-query-template-transact-sql.md)  
  
  
