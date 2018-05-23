---
title: sp_create_plan_guide (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_create_plan_guide
- sp_create_plan_guide_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_create_plan_guide
ms.assetid: 5a8c8040-4f96-4c74-93ab-15bdefd132f0
caps.latest.revision: 82
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 79e07848de5827f172e298f96d2ec55d30422eb5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="spcreateplanguide-transact-sql"></a>sp_create_plan_guide (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [ @name =] N'*plan_guide_name*"  
 Имя структуры плана. Имена структур планов ограничены областью текущей базы данных. *plan_guide_name* должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md) и не может начинаться со знака номера (#). Максимальная длина *plan_guide_name* равна 124 символам.  
  
 [ @stmt =] N'*statement_text*"  
 Инструкция языка [!INCLUDE[tsql](../../includes/tsql-md.md)], для которой создается структура плана. Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запроса оптимизатор поступает запрос, который соответствует *statement_text*, *plan_guide_name* вступает в силу. Для создания структуры плана для успешной работы *statement_text* должен быть указан в контексте, определяемом @type, @module_or_batch, и @params параметров.  
  
 *statement_text* должен быть представлен способом, позволяющим оптимизатору запросов сопоставить его с соответствующей инструкцией, содержащейся в пределах пакета или модуля, идентифицируемого по @module_or_batch и @params. Дополнительные сведения см. в разделе «Примечания». Размер *statement_text* ограничено только объемом доступной памяти сервера.  
  
 [@type =] N'{ОБЪЕКТА | SQL | ШАБЛОН} "  
 Тип сущности, в которой *statement_text* отображается. Это указывает контекст для сопоставления *statement_text* для *plan_guide_name*.  
  
 OBJECT  
 Указывает *statement_text* появляется в контексте [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимая процедура, скалярная функция, функция из нескольких инструкций табличное или [!INCLUDE[tsql](../../includes/tsql-md.md)] триггер DML в текущей базе данных.  
  
 SQL  
 Указывает *statement_text* появляется в контексте изолированной инструкции или пакета, который может быть отправлена на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] каким-либо способом. [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций по общим объектам языка среды CLR или расширенных хранимых процедур или с помощью инструкции EXEC EXEC N'*sql_string*", обрабатываются как пакеты на сервере и, следовательно, могут быть определены как @type **=** «SQL». Если указан SQL, указание запроса, PARAMETERIZATION {FORCED | ПРОСТОЙ} не может указываться в @hints параметра.  
  
 TEMPLATE  
 Указывает, что структура плана применяется к любым запросам, параметризированным в форме, заданной в *statement_text*. Если указан TEMPLATE только PARAMETERIZATION {FORCED | Указание ПРОСТОГО} запроса могут быть указаны в @hints параметра. Дополнительные сведения о структуры планов TEMPLATE см. в разделе [укажите параметризации запросов с помощью планов](../../relational-databases/performance/specify-query-parameterization-behavior-by-using-plan-guides.md).  
  
 [@module_or_batch =] {N'[ *schema_name*. ] *object_name*"| N'*batch_text*"| NULL}  
 Указывает имя объекта, в котором *statement_text* появляется, и текст пакета, в котором *statement_text* отображается. Текст пакета не может содержать инструкцию USE*базы данных* инструкции.  
  
 Структура плана совпадала с пакетом, переданным из приложения *batch_tex*t должно быть предоставлено в том же формате, символ к символу, в котором он передается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для упрощения соответствия формата внутренние преобразования не выполняются. Дополнительные сведения см. в разделе «Примечания».  
  
 [*schema_name*.] *object_name* указывает имя [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимая процедура, скалярная функция, функция из нескольких инструкций табличное или [!INCLUDE[tsql](../../includes/tsql-md.md)] триггер DML, который содержит *statement_text*. Если *имя_схемы* не указан, *schema_name* используется схема текущего пользователя. Если указано значение NULL и @type = «SQL», значение @module_or_batch присвоено значение @stmt. Если @type = "ШАБЛОНА **"**, @module_or_batch должен иметь значение NULL.  
  
 [ @params =] {N' *@parameter_name data_type* [,*.. .n* ]' | NULL}  
 Указывает определения всех параметров, внедренных в *statement_text*. @params применяется, только если одно из следующих установлено значение true:  
  
-   @type = 'SQL' или 'TEMPLATE'. Если «ШАБЛОН» @params не должен иметь значение NULL.  
  
-   *statement_text* передается с помощью процедуры sp_executesql и значение @params параметр указан, или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет внутреннюю отправку инструкции после ее параметризации. Отправка параметризованных запросов через API-интерфейсы базы данных (включая ODBC, OLE DB и ADO.NET) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выглядит как вызов процедуры sp_executesql либо API-процедуры серверного курсора, поэтому они также могут совпадать со структурой плана SQL или TEMPLATE.  
  
 *@parameter_name data_type* должны быть указаны в формате, точное оно передается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] либо с помощью процедуры sp_executesql или отправки после параметризации. Дополнительные сведения см. в разделе «Примечания». Если пакет не содержит параметров, необходимо указать значение NULL. Размер @params ограничивается только доступной памяти на сервере.  
  
 [@hints =] {N'OPTION (*query_hint* [,*.. .n* ])' | N'*XML_showplan*"| NULL}  
 N'OPTION (*query_hint* [,*.. .n* ])  
 Указывает предложение OPTION, чтобы присоединить к запросу, который соответствует @stmt. @hints должен синтаксически совпадает с предложением OPTION инструкции SELECT и может содержать любую допустимую последовательность указаний запроса.  
  
 N'*XML_showplan*"  
 План запроса в формате XML для применения в качестве указания.  
  
 Значение аргумента XML_showplan рекомендуется присвоить переменной, иначе каждый символ одиночной кавычки необходимо предварять дополнительным символом одиночной кавычки. См. пример Д.  
  
 NULL  
 Указывает, что любое существующее указание, заданное в предложении OPTION запроса, не применяется к запросу. Дополнительные сведения см. в разделе [предложение OPTION &#40;Transact-SQL&#41;](../../t-sql/queries/option-clause-transact-sql.md).  
  
## <a name="remarks"></a>Замечания  
 Аргументы процедуры sp_create_plan_guide должны задаваться в указанном порядке. При задании значений параметрам процедуры **sp_create_plan_guide**все имена параметров необходимо указывать явно или вообще не указывать. Например, если указан параметр **@name =**, необходимо также указать параметры **@stmt =**, **@type =** и т. д. Аналогично, если параметр **@name =** пропущен и указано только его значение, для остальных параметров также должны быть указаны только значения, но не имена. Имена аргументов приводятся исключительно в целях описания, чтобы помочь разобраться с синтаксисом. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не проверяет соответствие указанных имен параметров их позициям.  
  
 Можно создать несколько структур планов OBJECT или SQL для одного и того же запроса и пакета либо модуля. Однако только одна структура плана может быть включена в данный момент времени.  
  
 Нельзя создавать структуры планов типа OBJECT для значения @module_or_batch, ссылающегося на хранимую процедуру, функцию или триггер DML, который задает предложение WITH ENCRYPTION или является временным.  
  
 Попытка удаления или изменения функции, хранимой процедуры или триггера DML, на которые имеется ссылка в структуре плана (как включенных, так и отключенных), приводит к ошибке. Попытка удалить таблицу, для которой определен триггер, имеющий соответствующую ссылку в структуре плана, также вызывает ошибку.  
  
> [!NOTE]  
>  Структуру планов можно использовать не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md). Структуры планов видны в любом выпуске. Можно также присоединить базу данных, содержащую структуры планов, к любой версии. Структуры планов остаются нетронутыми при восстановлении или присоединении базы данных к обновленной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Следует тщательно взвешивать необходимость использования структур планов в каждой базе данных после выполнения обновления сервера.  
  
## <a name="plan-guide-matching-requirements"></a>Требования по соответствию для структур планов  
 Для структур планов, которые указывают @type = 'SQL' или @type = 'TEMPLATE' для должного соответствия запросу, значения для *batch_text* и  *@parameter_name data_type* [,*.. .n* ] необходимо указать в том же формате, совпадают с аналогичными им параметров приложения. Это означает, что необходимо предоставить текст пакета в точном соответствии с текстом, получаемым компилятором [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для захвата действительного текста пакета и параметра используется приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Дополнительные сведения см. в разделе [использование приложения SQL Server Profiler для создания и проверки руководств планов](../../relational-databases/performance/use-sql-server-profiler-to-create-and-test-plan-guides.md).  
  
 Если @type = 'SQL' и @module_or_batch имеет значение NULL, параметр @module_or_batch получает значение @stmt. Это означает, что значение для *statement_text* должны быть предоставлены в формате, символ к символу, в котором он передается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для упрощения соответствия формата внутренние преобразования не выполняются.  
  
 Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] совпадает со значением *statement_text* для *batch_text* и  *@parameter_name data_type* [,*.. .n* ], или Если @type = **"** ОБЪЕКТА", с текстом соответствующего запроса внутри аргумента *object_name*, не учитываются следующие элементы строки:  
  
-   Пробельные символы (знаки табуляции, пробелы, возвраты каретки и переводы строки) внутри строки.  
  
-   Комментарии (**--** или **/ \* \* /**).  
  
-   Точка с запятой (;) в конце строки.  
  
 Например [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно сопоставить *statement_text* строка `N'SELECT * FROM T WHERE a = 10'` следующим *batch_text*:  
  
 `N'SELECT *`  
  
 `FROM T`  
  
 `WHERE a=10'`  
  
 Однако та же строка не совпадет к этому *batch_text*:  
  
 `N'SELECT * FROM T WHERE b = 10'`  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пропускает знаки возврата каретки, перевода строки и пробелы внутри первого запроса. При рассмотрении второго запроса строки `WHERE b = 10` и `WHERE a = 10` считаются различными. Результат сравнения учитывает регистр и наличие диакритических знаков (даже в случае, когда в параметрах сортировки базы данных задана сортировка без учета регистра), за исключением тех случаев, когда используются ключевые слова, игнорирующие регистр. Сравнение выполняется без учета сокращенных форм ключевых слов. Например, ключевые слова `EXECUTE`, `EXEC` и `execute` являются эквивалентными.  
  
## <a name="plan-guide-effect-on-the-plan-cache"></a>Влияние структуры плана на кэш планов  
 Создание структуры плана в модуле стирает план запроса для этого модуля из кэша планов. Создание структуры плана типа OBJECT или SQL в потоке стирает план запроса для потока, который имеет такое же значение хеш-функции. Создание структуры плана типа TEMPLATE стирает все потоки с одним оператором из кэша планов через базу данных.  
  
## <a name="permissions"></a>Разрешения  
 Для создания структуры плана типа OBJECT необходимо разрешение ALTER на соответствующий объект. Чтобы создать структуру плана типа SQL или TEMPLATE, необходимо обладать разрешением ALTER на текущую базу данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-plan-guide-of-type-object-for-a-query-in-a-stored-procedure"></a>A. Создание структуры плана типа OBJECT для запроса в хранимой процедуре  
 В приведенном ниже примере создается структура плана, с которой сопоставляется запрос, выполняемый в контексте хранимой процедуры приложения, а также происходит применение к запросу указания `OPTIMIZE FOR`.  
  
 Ниже приведена хранимая процедура.  
  
```  
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
  
```  
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
  
```  
SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC;  
```  
  
 Для предотвращения создания по данному запросу параллельного плана выполнения необходимо создать следующую структуру плана.  
  
```  
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
>  Значения постоянных литералов аргумента `@stmt`, передаваемого в процедуру sp_get_query_template, определяют тип данных для аргумента, заменяющего указанные литералы. Это влияет на совпадение структур планов. Возможно, придется создать несколько структур плана для обработки различных диапазонов значений аргумента.  
  
### <a name="d-creating-a-plan-guide-on-a-query-submitted-by-using-an-api-cursor-request"></a>Г. Создание структуры плана на основе запроса, переданного с помощью запроса курсора API  
 Структуры планов могут совпадать с запросами, передаваемыми с помощью процедур серверных курсоров API. К указанным процедурам относятся sp_cursorprepare, sp_cursorprepexec и sp_cursoropen. Приложения, использующие API-интерфейсы ADO, OLE DB и ODBC, часто связываются с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи серверных курсоров API. Вызов процедур серверного курсора API-интерфейса можно увидеть в трассировках приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], просматривая событие трассировки SQL Profiler RPC:Starting.  
  
 Допустим, что для запроса, настраиваемого с помощью структуры плана, в событии трассировки RPC:Starting приложения SQL Profiler имеются следующие данные.  
  
```  
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
  
```  
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
    @hints =@xml_showplan;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Руководства планов](../../relational-databases/performance/plan-guides.md)   
 [sp_control_plan_guide (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql.md)   
 [sys.plan_guides (Transact-SQL)](../../relational-databases/system-catalog-views/sys-plan-guides-transact-sql.md)   
 [Компонент Database Engine хранимой процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)   
 [sys.fn_validate_plan_guide (Transact-SQL)](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md)   
 [sp_get_query_template &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-query-template-transact-sql.md)  
  
  
