---
title: "Создание функции (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
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
- FUNCTION
- CREATE FUNCTION
- CREATE_FUNCTION_TSQL
- FUNCTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- invoking functions
- extended stored procedures [SQL Server], functions
- table-valued parameters
- user-defined functions [SQL Server], creating
- CLR functions [SQL Server]
- CREATE FUNCTION statement
- nondeterministic functions
- user-defined data types
- functions [SQL Server], creating
- inline table-valued functions [SQL Server]
- multi-statement table-valued functions [SQL Server]
- table-valued functions [SQL Server], CREATE FUNCTION
- parameters [SQL Server], functions
- nesting user-defined functions
- deterministic functions
- scalar-valued functions
- functions [SQL Server], invoking
ms.assetid: 864b393f-225f-4895-8c8d-4db59ea60032
caps.latest.revision: 162
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: c74e3a3322dcc2268fa8e386fda5d55f59be98c5
ms.contentlocale: ru-ru
ms.lasthandoff: 10/24/2017

---
# <a name="create-function-transact-sql"></a>CREATE FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает определяемую пользователем функцию в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Определяемая пользователем функция представляет собой подпрограмму [!INCLUDE[tsql](../../includes/tsql-md.md)] или среды CLR, которая принимает параметры, выполняет действия, такие как сложные вычисления, а затем возвращает результат этих действий в виде значения. Возвращаемое значение может быть скалярным значением или таблицей. При помощи этой инструкции можно создать подпрограмму, которую можно повторно использовать следующими способами.  
  
-   В инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)], например SELECT.  
  
-   В приложениях, вызывающих функцию.  
  
-   В определении другой пользовательской функции.  
  
-   Для параметризации представления или улучшения функциональности индексированного представления.  
  
-   Для определения столбца таблицы.  
  
-   Для определения ограничения CHECK на столбец.  
  
-   Для замены хранимой процедуры.  
  
-   Использовать встроенную функцию в качестве предиката фильтра для политики безопасности  
  
> [!NOTE]  
>  В этом разделе рассматривается интеграция со средой CLR .NET Framework в SQL Server. Интеграция со средой CLR не применяется к базе данных SQL Azure.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Transact-SQL Scalar Function Syntax  
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ][ type_schema_name. ] parameter_data_type   
    [ = default ] [ READONLY ] }   
    [ ,...n ]  
  ]  
)  
RETURNS return_data_type  
    [ WITH <function_option> [ ,...n ] ]  
    [ AS ]  
    BEGIN   
        function_body   
        RETURN scalar_expression  
    END  
[ ; ]  
```  
  
```  
-- Transact-SQL Inline Table-Valued Function Syntax   
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ] [ type_schema_name. ] parameter_data_type   
    [ = default ] [ READONLY ] }   
    [ ,...n ]  
  ]  
)  
RETURNS TABLE  
    [ WITH <function_option> [ ,...n ] ]  
    [ AS ]  
    RETURN [ ( ] select_stmt [ ) ]  
[ ; ]  
  
```  
  
```  
-- Transact-SQL Multi-Statement Table-Valued Function Syntax  
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ] [ type_schema_name. ] parameter_data_type   
    [ = default ] [READONLY] }   
    [ ,...n ]  
  ]  
)  
RETURNS @return_variable TABLE <table_type_definition>  
    [ WITH <function_option> [ ,...n ] ]  
    [ AS ]  
    BEGIN   
        function_body   
        RETURN  
    END  
[ ; ]  
  
```  

```  
-- Transact-SQL Function Clauses   
<function_option>::=   
{  
    [ ENCRYPTION ]  
  | [ SCHEMABINDING ]  
  | [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]  
  | [ EXECUTE_AS_Clause ]  
}  
  
<table_type_definition>:: =   
( { <column_definition> <column_constraint>   
  | <computed_column_definition> }   
    [ <table_constraint> ] [ ,...n ]  
)   
<column_definition>::=  
{  
    { column_name data_type }  
    [ [ DEFAULT constant_expression ]   
      [ COLLATE collation_name ] | [ ROWGUIDCOL ]  
    ]  
    | [ IDENTITY [ (seed , increment ) ] ]  
    [ <column_constraint> [ ...n ] ]   
}  
  
<column_constraint>::=   
{  
    [ NULL | NOT NULL ]   
    { PRIMARY KEY | UNIQUE }  
      [ CLUSTERED | NONCLUSTERED ]   
      [ WITH FILLFACTOR = fillfactor   
        | WITH ( < index_option > [ , ...n ] )  
      [ ON { filegroup | "default" } ]  
  | [ CHECK ( logical_expression ) ] [ ,...n ]  
}  
  
<computed_column_definition>::=  
column_name AS computed_column_expression   
  
<table_constraint>::=  
{   
    { PRIMARY KEY | UNIQUE }  
      [ CLUSTERED | NONCLUSTERED ]   
      ( column_name [ ASC | DESC ] [ ,...n ] )  
        [ WITH FILLFACTOR = fillfactor   
        | WITH ( <index_option> [ , ...n ] )  
  | [ CHECK ( logical_expression ) ] [ ,...n ]  
}  
  
<index_option>::=  
{   
    PAD_INDEX = { ON | OFF }   
  | FILLFACTOR = fillfactor   
  | IGNORE_DUP_KEY = { ON | OFF }  
  | STATISTICS_NORECOMPUTE = { ON | OFF }   
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS ={ ON | OFF }   
}  
```  
  
```  
-- CLR Scalar Function Syntax  
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
( { @parameter_name [AS] [ type_schema_name. ] parameter_data_type   
    [ = default ] }   
    [ ,...n ]  
)  
RETURNS { return_data_type }  
    [ WITH <clr_function_option> [ ,...n ] ]  
    [ AS ] EXTERNAL NAME <method_specifier>  
[ ; ]  
```  
  
```  
-- CLR Table-Valued Function Syntax  
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
( { @parameter_name [AS] [ type_schema_name. ] parameter_data_type   
    [ = default ] }   
    [ ,...n ]  
)  
RETURNS TABLE <clr_table_type_definition>   
    [ WITH <clr_function_option> [ ,...n ] ]  
    [ ORDER ( <order_clause> ) ]  
    [ AS ] EXTERNAL NAME <method_specifier>  
[ ; ]  
```  

```  
-- CLR Function Clauses  
<order_clause> ::=   
{  
   <column_name_in_clr_table_type_definition>  
   [ ASC | DESC ]   
} [ ,...n]   
  
<method_specifier>::=  
    assembly_name.class_name.method_name  
  
<clr_function_option>::=  
}  
    [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]  
  | [ EXECUTE_AS_Clause ]  
}  
  
<clr_table_type_definition>::=   
( { column_name data_type } [ ,...n ] )  
  
```  
  
```  
-- In-Memory OLTP: Syntax for natively compiled, scalar user-defined function  
CREATE [ OR ALTER ] FUNCTION [ schema_name. ] function_name   
 ( [ { @parameter_name [ AS ][ type_schema_name. ] parameter_data_type   
    [ NULL | NOT NULL ] [ = default ] [ READONLY ] }   
    [ ,...n ]   
  ]   
)   
RETURNS return_data_type  
     WITH <function_option> [ ,...n ]   
    [ AS ]   
    BEGIN ATOMIC WITH (set_option [ ,... n ])   
        function_body   
        RETURN scalar_expression  
    END  
  
<function_option>::=   
{  
  |  NATIVE_COMPILATION   
  |  SCHEMABINDING   
  | [ EXECUTE_AS_Clause ]   
  | [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]   
}  
  
```  
  
## <a name="arguments"></a>Аргументы
*ИЛИ ALTER*  
 **Применяется к**: Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1).  
  
 Условно изменяет функции только в том случае, если он уже существует. 
 
> [!NOTE]  
>  Дополнительный синтаксис [или ALTER] для среды CLR доступен, начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU1.   
 
 *schema_name*  
 Имя схемы, к которой принадлежит определяемая пользователем функция.  
  
 *имя функции*  
 Имя определяемой пользователем функции. Имена функций должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md) и должно быть уникальным в пределах базы данных и схемы.  
  
> [!NOTE]  
>  Даже при отсутствии аргументов скобки после имени функции обязательны.  
  
 @*имя_параметра*  
 Аргумент пользовательской функции. Может быть объявлен один или несколько аргументов.  
  
 Для функций допускается не более 2 100 параметров. При выполнении функции значение каждого из объявленных параметров должно быть указано пользователем, если для них не определены значения по умолчанию.  
  
 Определяет имя параметра, используя знак @ как первый символ. Имя параметра должно соответствовать правилам для идентификаторов. Параметры являются локальными в пределах функции, в разных функциях могут быть использованы одинаковые имена параметров. Аргументы могут использоваться только вместо констант. Они не могут использоваться вместо имен таблиц, имен столбцов или имен других объектов базы данных.  
  
> [!NOTE]  
>  Параметры ANSI_WARNINGS не годятся для передачи в хранимые процедуры, пользовательские функции и при объявлении и установке переменных в пакетных инструкциях. Например, если переменная определена как **char(3)**и присвоено значение длиннее трех символов, данные будут усечены до определенного размера, а операция вставки или обновления инструкция была выполнена успешно.  
  
 [ *type_schema_name*. ] *parameter_data_type*  
 Тип данных параметра (возможно, с указанием схемы, которой он принадлежит). Для [!INCLUDE[tsql](../../includes/tsql-md.md)] допускаются все типы данных, включая определяемые пользователем типы среды CLR и определяемые пользователем табличные типы, функции, за исключением **timestamp** тип данных. Для функций CLR допустимы все типы данных, включая определяемые пользователем типы среды CLR, за исключением **текст**, **ntext**, **изображения**, определяемых пользователем табличных типов и  **Отметка времени** типов данных. Нескалярные типы **курсор** и **таблицы**, не может быть указан как тип данных параметра в любом [!INCLUDE[tsql](../../includes/tsql-md.md)] ни для функций CLR.  
  
 Если *type_schema_name* не указан, [!INCLUDE[ssDE](../../includes/ssde-md.md)] ищет *scalar_parameter_data_type* в следующем порядке:  
  
-   в схеме, содержащей имена системных типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];  
  
-   в установленной по умолчанию для текущего пользователя схеме в текущей базе данных;  
  
-   Схема **dbo** в текущей базе данных.  
  
 [=*по умолчанию* ]  
 Значение по умолчанию для аргумента. Если *по умолчанию* определено, функция может быть выполнена без указания значения для этого параметра.  
  
> [!NOTE]  
>  Значения параметров по умолчанию может быть указано для функций CLR за исключением **varchar(max)** и **varbinary(max)** типов данных.  
  
 Если параметр функции имеет значение по умолчанию, то для него должно быть указано ключевое слово DEFAULT для получения функцией значения по умолчанию. Применение ключевого слова DEFAULT следует отличать от использования аргументов со значениями по умолчанию в хранимых процедурах, когда не указанный аргумент неявно принимает значение по умолчанию. Однако ключевое слово DEFAULT не требуется при вызове скалярной функции с помощью инструкции EXECUTE.  
  
 READONLY  
 Указывает, что параметр не может быть обновлен или изменен при определении функции. Если тип параметра является определяемым пользователем табличным типом, то должно быть указано ключевое слово READONLY.  
  
 *return_data_type*  
 Возвращаемое значение скалярной пользовательской функции. Для [!INCLUDE[tsql](../../includes/tsql-md.md)] допускаются функции, все типы данных, включая определяемые пользователем типы среды CLR, за исключением **timestamp** тип данных. Для функций CLR допустимы все типы данных, включая определяемые пользователем типы среды CLR, за исключением **текст**, **ntext**, **изображения**, и **timestamp**типы данных. Нескалярные типы **курсор** и **таблицы**, нельзя использовать как тип возвращаемых данных либо [!INCLUDE[tsql](../../includes/tsql-md.md)] ни для функций CLR.  
  
 *function_body*  
 Указывает серию инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)], совместная работа которых не вызывает побочных эффектов, например изменения содержимого таблиц, и формирует значение функции. *function_body* используется только в скалярных функциях и из нескольких инструкций функциях, возвращающих табличные значения.  
  
 Для скалярных функций *тело_функции* представляет собой ряд [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций, которые в совокупности вычисляют скалярное значение.  
  
 В функции из нескольких инструкций табличные *тело_функции* представляет собой ряд [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций, заполняющих таблицы возвращаемую переменную.  
  
 *scalar_expression*  
 Указывает скалярное значение, возвращаемое скалярной функцией.  
  
 TABLE  
 Указывает, что возвращаемым значением функции с табличным значением, является таблица. Только константы и @*local_variables* могут быть переданы функции, возвращающие табличные значения.  
  
 Во встроенных функциях с табличным значением возвращаемое значение TABLE определяется при использовании единственной инструкции SELECT. Встроенные функции не имеют соответствующих возвращаемых переменных.  
  
 В функции из нескольких инструкций табличные @*return_variable* является переменная TABLE используется для хранения и накопления строк, которые должны возвращаться как значение функции. @*return_variable* может быть указан только для [!INCLUDE[tsql](../../includes/tsql-md.md)] функции, но не для функций CLR.  
  
> [!WARNING]  
>  Присоединение к табличным табличное значение функции в **FROM** предложение возможна, но может снизить производительность. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может использовать все оптимизированные методы для некоторых инструкций, которые можно включить в такую функцию, и в результате план запроса оказывается неоптимальным. Чтобы получить наилучшую производительность, по возможности задавайте соединения не между функциями, а между базовыми таблицами.  
  
 *select_stmt*  
 Единственная инструкция SELECT, которая определяет возвращаемое значение встроенной функции, возвращающей табличное значение.  
  
 ПОРЯДОК (\<order_clause >) указывает порядок, в котором возвращаются результаты из функции, возвращающие табличные значения. Дополнительные сведения см. в подразделе «Руководство по использованию порядка сортировки» далее в этом разделе.  
  
 ВНЕШНЕЕ имя \<method_specifier > *assembly_name*. *class_name*. *имя_метода* **применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает сборку и метод, на которые должно ссылаться имя создаваемой функции.  
  
-   *assembly_name* -должно соответствовать значению в `name` столбец   
    `SELECT * FROM sys.assemblies;`.  
    Это имя, которое использовалось в инструкции `CREATE ASSEMBLY`.  
  
-   *class_name* -должно соответствовать значению в `assembly_name` столбец  
    `SELECT * FROM sys.assembly_modules;`.  
    Часто это значение содержит точку или пунктир. В таких случаях Transact-SQL синтаксис требует привязаны значение с помощью пары квадратные скобки [] или с помощью пары двойных кавычек «».  
  
-   *имя_метода* -должно соответствовать значению в `method_name` столбец   
    `SELECT * FROM sys.assembly_modules;`.  
    Метод должен быть статическим.  
  
 В типичном примере для библиотеки MyFood.DLL, в которой все типы находятся в пространстве имен MyFood, значение `EXTERNAL NAME` может быть следующим:   
`MyFood.[MyFood.MyClass].MyStaticMethod`  
  
> [!NOTE]  
>  По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не производит выполнение кода CLR. Можно создавать, изменять и удалять объекты базы данных, которые ссылаются на модули среды CLR; Однако нельзя выполнять эти ссылки в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до включения [параметр clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md). Чтобы включить этот параметр, используйте [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
 *\<*table_type_definition *>*  ({ \<column_definition > \<column_constraint > | \<computed_column_definition >}    [ \<table_constraint >] [ ,... *n*  ]) Определяет тип данных таблицы для [!INCLUDE[tsql](../../includes/tsql-md.md)] функции. Объявление таблицы включает определения столбцов, а также ограничений для столбцов и таблиц. Таблица всегда помещается в первичную файловую группу.  
  
 \<clr_table_type_definition > ({ *column_name**data_type* } [ ,... *n*  ]) **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([Предварительная версия в некоторых регионах](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)). |  
  
 Определяет табличные типы данных для функции CLR. Объявление таблицы включает только имена столбцов и типы данных. Таблица всегда помещается в первичную файловую группу.  
  
 ЗНАЧЕНИЕ NULL | НЕ NULL  
 Поддерживается только для скомпилированных в собственном коде скалярные определяемые пользователем функции. Дополнительные сведения см. в разделе [скалярные определяемые пользователем функции для In-Memory OLTP](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
 NATIVE_COMPILATION  
 Указывает, является ли определяемая пользователем функция скомпилирован в собственном коде. Этот аргумент является обязательным для скомпилированных в собственном коде скалярные определяемые пользователем функции.  
  
 BEGIN ATOMIC С  
 Поддерживается только для скомпилированных в собственном коде, скалярные определяемые пользователем функции, и является обязательным. Дополнительные сведения см. в статье [Atomic Blocks](../../relational-databases/in-memory-oltp/atomic-blocks-in-native-procedures.md).  
  
 SCHEMABINDING  
 Аргумент SCHEMABINDING требуется для скомпилированных в собственном коде скалярные определяемые пользователем функции.  
  
 EXECUTE AS  
 EXECUTE AS является обязательным для скомпилированных в собственном коде скалярные определяемые пользователем функции.  
  
 **\<function_option >:: = и \<clr_function_option >:: =** 
  
 Указывает, что функция будет иметь один или несколько из следующих параметров.  
  
 ENCRYPTION  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает, что компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] преобразует исходный текст инструкции CREATE FUNCTION в скрытый формат. Выходные данные запутывания не видны непосредственно ни в одном представлении каталога. Пользователи, не имеющие доступа к системным таблицам или файлам баз данных, не смогут получить скрытый текст. Тем не менее, текст будет доступен привилегированным пользователям, которые либо смогут обращаться к системным таблицам через [порт выделенного административного Соединения](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md) или непосредственный доступ к файлам базы данных. Кроме того, пользователи, имеющие право на подключение отладчика к серверному процессу, могут получить исходный текст процедуры из памяти во время выполнения. Дополнительные сведения о доступе к системным метаданным см. в разделе [настроек видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
 Использование этого параметра препятствует публикации данной функции как части репликации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот параметр для функций CLR указывать нельзя.  
  
 SCHEMABINDING  
 Указывает, что функция привязана к объектам базы данных, которые содержат ссылки на нее. Если аргумент SCHEMABINDING указан, нельзя изменить базовые объекты таким способом, который может повлиять на определение функции. Сначала нужно изменить или удалить само определение функции, чтобы удалить зависимости от объекта, который требуется изменить.  
  
 Привязка функции к ссылающимся на нее объектам удаляется в следующих случаях: 
  
-   При удалении функции.  
  
-   При изменении функции инструкцией ALTER, если не указан параметр SCHEMABINDING.  
  
 Функция может быть привязана к схеме только в том случае, если выполняются следующие условия.  
  
-   Функция является функцией [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Пользовательские функции и представления, на которые ссылается данная функция, также привязаны к схеме.  
  
-   Объекты, на которые ссылается функция, указываются двухкомпонентными именами.  
  
-   Функция и объекты, на которые она ссылается, относятся к одной и той же базе данных.  
  
-   Пользователь, выполняющий инструкцию CREATE FUNCTION, имеет разрешение REFERENCES на объекты базы данных, на которые ссылается функция.  
  
 ВОЗВРАЩАЕТ ЗНАЧЕНИЕ NULL НА NULL INPUT | **ВЫЗЫВАЕТСЯ НА ВХОДЕ ЗНАЧЕНИЕ NULL**  
 Указывает **OnNULLCall** атрибут скалярной функции. Если данный аргумент не указан, по умолчанию предполагается CALLED ON NULL INPUT. Это означает, что текст функции выполняется даже в том случае, если в качестве аргумента передано значение NULL.  
  
 Если атрибут RETURNS NULL ON NULL INPUT указан для функции CLR, это означает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может вернуть NULL, не вызывая при этом тело функции в том случае, если в качестве какого-либо из аргументов указано значение NULL. Если метод функции CLR указан в \<method_specifier > уже имеет пользовательский атрибут, который указывает RETURNS NULL ON NULL INPUT, но инструкция CREATE FUNCTION определяет CALLED ON NULL INPUT, принимает инструкции CREATE FUNCTION более высокий приоритет. **OnNULLCall** атрибут не может быть указан для функций CLR с табличным. 
  
 Предложение EXECUTE AS  
 Указывает контекст безопасности, в котором выполняется определяемая пользователем функция. Иными словами, есть возможность управлять тем, какую учетную запись пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует при определении разрешений на объекты базы данных, на которые ссылается функция.  
  
> [!NOTE]  
>  Предложение EXECUTE AS не может быть указано для встроенных пользовательских функций.  
  
 Дополнительные сведения см. в разделе [Предложение EXECUTE AS (Transact-SQL)](../../t-sql/statements/execute-as-clause-transact-sql.md).  
  
 **\<column_definition >:: =** 
  
 Определяет тип данных таблицы. Декларация таблицы включает определения столбцов и ограничений. Для функций CLR только *column_name* и *data_type* можно указать.  
  
 *column_name*  
 Имя столбца в таблице. Имена столбцов должны соответствовать правилам для идентификаторов и быть уникальными в рамках таблицы. *column_name* может содержать от 1 до 128 символов.  
  
 *Тип данных*  
 Указывает тип данных столбца. Для [!INCLUDE[tsql](../../includes/tsql-md.md)] допускаются функции, все типы данных, включая определяемые пользователем типы среды CLR, за исключением **timestamp**. Для функций CLR допустимы все типы данных, включая определяемые пользователем типы среды CLR, за исключением **текст**, **ntext**, **изображения**, **char**, **varchar**, **varchar(max)**, и **timestamp**. Нескалярный тип **курсор** нельзя использовать как тип данных столбца, либо [!INCLUDE[tsql](../../includes/tsql-md.md)] ни для функций CLR.  
  
 По умолчанию *constant_expression*  
 Указывает значение, присваиваемое столбцу в случае отсутствия явно заданного значения при вставке. *constant_expression* константа, NULL или значением системной функции. Определения DEFAULT могут применяться к любым столбцам, кроме тех, которые имеют свойство IDENTITY. Предложение DEFAULT не может быть указано для функций CLR с табличным значением.  
  
 COLLATE *collation_name*  
 Задает параметры сортировки для столбца. Если не указано, столбцу назначаются параметры сортировки, принятые в базе данных по умолчанию. Именем параметров сортировки может быть либо имя параметров сортировки Windows, либо имя параметров сортировки SQL. Перечень и Дополнительные сведения о параметрах сортировки см. в разделе [имя параметров сортировки Windows &#40; Transact-SQL &#41; ](../../t-sql/statements/windows-collation-name-transact-sql.md) и [SQL Server Collation Name &#40; Transact-SQL &#41; ](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 Предложение COLLATE можно использовать для изменения параметров сортировки только для столбцов **char**, **varchar**, **nchar**, и **nvarchar** типов данных.  
  
 Предложение COLLATE не может быть указано для функций CLR с табличным значением.  
  
 ROWGUIDCOL  
 Показывает, что новый столбец является строковым столбцом идентификаторов GUID. Только один **uniqueidentifier** столбца в каждой таблице можно определить как столбец ROWGUIDCOL. Свойство ROWGUIDCOL может присваиваться только **uniqueidentifier** столбца.  
  
 Свойство ROWGUIDCOL не обеспечивает уникальности значений, хранимых в столбце. Кроме того, данное свойство не производит автоматическое формирование значений для новых строк, вставляемых в таблицу. Для создания уникальных значений произвольного столбца используйте функцию NEWID в инструкции INSERT. Может быть указано значение по умолчанию. При этом функция NEWID не может быть указана в качестве значения по умолчанию.  
  
 IDENTITY  
 Указывает, что новый столбец является столбцом идентификаторов. При добавлении в таблицу новой строки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует для столбца уникальное, последовательное значение. Столбцы идентификаторов обычно используются с ограничением PRIMARY KEY для поддержания уникальности идентификаторов строк в таблице. Свойство IDENTITY может назначаться **tinyint**, **smallint**, **int**, **bigint**, **decimal(p,0)**, или **numeric(p,0)** столбцы. Для каждой таблицы можно создать только один столбец идентификаторов. Ограниченные значения по умолчанию и ограничения DEFAULT не могут использоваться в столбце идентификаторов. Необходимо указать оба *начальное значение* и *приращения* и ни одного. Если ничего не указано, применяется значение по умолчанию (1,1).  
  
 Предложение IDENTITY не может быть указано для функций CLR с табличным значением.  
  
 *Начальное значение*  
 Целочисленное значение, присваиваемое первой строке таблицы.  
  
 *приращение*  
 Целочисленное значение, чтобы добавить *начальное значение* для каждой последующей строки в таблице.  
  
 **\<column_constraint >:: = и \< table_constraint >:: =** 
  
 Определяет ограничение для указанного столбца или таблицы. Для функций CLR единственное допустимое ограничение — NULL. Именованные ограничения недопустимы.  
  
 NULL | NOT NULL  
 Определяет, допустимы ли для столбца значения NULL. Параметр NULL не является ограничением в строгом смысле слова, но может быть указан так же, как и NOT NULL. Ограничение NOT NULL не может быть указано для функций CLR с табличным значением.  
  
 PRIMARY KEY  
 Ограничение, обеспечивающее целостность сущностей для указанного столбца через уникальный индекс. В возвращающих табличное значение пользовательских функциях ограничение PRIMARY KEY может быть создано только для одного столбца таблицы. Ограничение PRIMARY KEY не может быть указано для функций CLR с табличным значением.  
  
 UNIQUE  
 Ограничение, которое обеспечивает целостность сущностей для указанного столбца или столбцов с помощью уникального индекса. В таблице может быть несколько ограничений UNIQUE. Ограничение UNIQUE не может быть указано для функций CLR с табличным значением.  
  
 CLUSTERED | NONCLUSTERED  
 Указывает, что для ограничения PRIMARY KEY или UNIQUE создается кластеризованный или некластеризованный индекс. Ограничения PRIMARY KEY используют параметр CLUSTERED, а ограничения UNIQUE используют параметр NONCLUSTERED.  
  
 Параметр CLUSTERED может быть указан только для одного ограничения. Если параметр CLUSTERED указан для ограничения UNIQUE и указано ограничение PRIMARY KEY, то PRIMARY KEY использует NONCLUSTERED.  
  
 Параметры СLUSTERED и NONСLUSTERED не могут быть указаны для функций CLR с табличным значением.  
  
 CHECK  
 Ограничение, обеспечивающее целостность домена путем ограничения возможных значений, которые могут быть введены в столбец или столбцы. Ограничения CHECK не могут быть указаны для функций CLR с табличным значением.  
  
 *Logical_Expression*  
 Логическое выражение, возвращающее значения TRUE или FALSE.  
  
 **\<computed_column_definition >:: =**  
  
 Указывает вычисляемый столбец. Дополнительные сведения о вычисляемых столбцах см. в разделе [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).  
  
 *column_name*  
 Имя вычисляемого столбца.  
  
 *computed_column_expression*  
 Выражение, определяющее значение вычисляемого столбца.  
  
 **\<index_option >:: =**  
  
 Указывает параметры индекса для индекса PRIMARY KEY или UNIQUE. Дополнительные сведения о параметрах индекса см. в разделе [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
 PAD_INDEX = {ON | **OFF** }  
 Определяет разреженность индекса. Значение по умолчанию — OFF.  
  
 FILLFACTOR = *fillfactor*  
 Определяет величину в процентах, указывающую, насколько компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] должен заполнять конечный уровень каждой страницы индекса во время создания или изменения индекса. *значение коэффициента заполнения* должно быть целым числом от 1 до 100. Значение по умолчанию равно 0.  
  
 IGNORE_DUP_KEY = {ON | **OFF** }  
 Определяет ответ на ошибку, случающуюся, когда операция вставки пытается вставить в уникальный индекс повторяющиеся значения ключа. Параметр IGNORE_DUP_KEY применяется только к операциям вставки, производимым после создания или перестроения индекса. Значение по умолчанию — OFF.  
  
 STATISTICS_NORECOMPUTE = {ON | **OFF** }  
 Указывает, выполнялся ли перерасчет статистики распределения. Значение по умолчанию — OFF.  
  
 ALLOW_ROW_LOCKS = { **ON** | {OFF}  
 Указывает, разрешена ли блокировка строк. Значение по умолчанию — ON.  
  
 ALLOW_PAGE_LOCKS = { **ON** | {OFF}  
 Указывает, разрешена ли блокировка страниц. Значение по умолчанию — ON.  
  
## <a name="best-practices"></a>Рекомендации  
 Если определяемая пользователем функция создан без применения предложения SCHEMABINDING, то изменения базовых объектов могут повлиять на определение функции и привести к непредвиденным результатам при вызове функции. Рекомендуется реализовать один из следующих методов, чтобы обеспечить, что функция не устареет из-за изменения ее базовых объектов.  
  
-   Укажите при создании функции предложение WITH SCHEMABINDING. Это обеспечит невозможность изменения объектов, на которые ссылается определение функции, если при этом не изменяется сама функция.  
  
-   Выполнение [sp_refreshsqlmodule](../../relational-databases/system-stored-procedures/sp-refreshsqlmodule-transact-sql.md) хранимую процедуру после изменения любого объекта, который указан в определении функции.  
  
## <a name="data-types"></a>Типы данных  
 Если параметры указаны в функции CLR, они должны быть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов, как определено ранее для *scalar_parameter_data_type*. Сведения о сравнении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] системных типов данных в типы данных интеграции со средой CLR или [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] типами среды CLR данных, в разделе [сопоставления данных о параметрах CLR](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).  
  
 Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ссылаться на нужный метод, если он переопределен в классе, метод указанным в \<method_specifier >, должен иметь следующие характеристики: 
  
-   Получают одинаковое число параметров, которое указано в [ ,...*n* ].  
  
-   Принимать все параметры по значению, а не по ссылке.  
  
-   Принимать типы параметров, совместимые с теми, что указаны в функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если тип возвращаемых данных функции CLR указан табличный тип (RETURNS TABLE), тип возвращаемых данных метода в \<method_specifier > должен иметь тип **IEnumerator** или **IEnumerable**, и предполагается, что интерфейс реализуется на автора функции. В отличие от [!INCLUDE[tsql](../../includes/tsql-md.md)] функции, функции CLR не могут содержать ограничений PRIMARY KEY, UNIQUE и CHECK в \<table_type_definition >. Типы данных столбцов, указанных в \<table_type_definition > должны совпадать с типами соответствующих столбцов результирующего набора, возвращаемого методом в \<method_specifier > во время выполнения. Проверка типов на этапе создания функции не производится. 
  
 Дополнительные сведения о программировании функций CLR см. в разделе [определяемые пользователем функции](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md).  
  
## <a name="general-remarks"></a>Общие замечания  
 Скалярная функция может быть указана в любом месте вместо скалярного выражения, в том числе в вычисляемых столбцах и определениях ограничений CHECK. Скалярные функции также могут быть выполнены с помощью [EXECUTE](../../t-sql/language-elements/execute-transact-sql.md) инструкции. Скалярные функции должны вызываться с помощью как минимум двухкомпонентного имени. Дополнительные сведения о многокомпонентных именах см. в разделе [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md). Функция, возвращающая табличное значение, может быть вызвана в любом месте, где допускаются табличные выражения, — в предложении FROM инструкций SELECT, INSERT, UPDATE и DELETE. Дополнительные сведения см. в разделе [выполнение пользовательских функций](../../relational-databases/user-defined-functions/execute-user-defined-functions.md).  
  
## <a name="interoperability"></a>Совместимость  
 В функциях допустимы следующие инструкции.  
  
-   Инструкции присваивания.  
  
-   Инструкции управления потоком, за исключением инструкций TRY...CATCH.  
  
-   Инструкции DECLARE, объявляющие локальные переменные и локальные курсоры.  
  
-   Инструкции SELECT, которые содержат списки выбора с выражениями, присваивающими значения локальным переменным.  
  
-   Операции над локальными курсорами, которые объявляются, открываются, закрываются и освобождаются в теле функции. Допустимы только те инструкции FETCH, которые предложением INTO присваивают значения локальным переменным. Инструкции FETCH, возвращающие данные клиенту, недопустимы.  
  
-   Инструкции INSERT, UPDATE и DELETE, которые изменяют локальные табличные переменные.  
  
-   Инструкции EXECUTE, вызывающие расширенные хранимые процедуры.  
  
-   Дополнительные сведения см. в разделе [создание определяемых пользователем функций &#40; компонент Database Engine &#41;](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md).  
  
### <a name="computed-column-interoperability"></a>Взаимодействие с вычисляемыми столбцами  
 Функции имеют перечисленные ниже свойства. Значения этих свойств определяют, может ли данная функция быть указана в вычисляемых столбцах, которые могут быть материализованными или индексированными.  
  
|Свойство|Description|Примечания|  
|--------------|-----------------|-----------|  
|**IsDeterministic**|Функция детерминированная или недетерминированная.|Для детерминированных функций разрешается доступ к локальным данным. Например, функция, которая при вызове с одними и теми же параметрами и в одном том же состоянии базы данных всегда возвращает один и тот же результат, называется детерминированной.|  
|**IsPrecise**|Функция точная или неточная.|Неточные функции содержат такие операции, как операции с плавающей запятой.|  
|**IsSystemVerified**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может проверять свойства точности и детерминированности функций.||  
|**SystemDataAccess**|Функции, производящие доступ к системным данным (системным каталогам или виртуальным системным таблицам) в локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].||  
|**UserDataAccess**|Функция производит доступ к данным пользователя в локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Сюда входят определяемые пользователем и временные таблицы, но не табличные переменные.|  
  
 Для функций [!INCLUDE[tsql](../../includes/tsql-md.md)] свойства точности и детерминизма [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет автоматически. Свойства доступа к данным и детерминированности функций CLR могут быть указаны пользователем. Дополнительные сведения см. в разделе [Общие сведения о пользовательских интеграции со средой CLR атрибутов](http://msdn.microsoft.com/library/ecf5c097-0972-48e2-a9c0-b695b7dd2820).  
  
 Для отображения текущих значений этих свойств используйте [OBJECTPROPERTYEX](../../t-sql/functions/objectpropertyex-transact-sql.md).  
  
 Функции необходимо создавать с детерминированной привязкой схемы.  
  
 Вычисляемый столбец, который обращается к определяемой пользователем функции, может быть включен в индекс, если функция имеет следующие значения свойств:  
  
-   **IsDeterministic** = true  
  
-   **IsSystemVerified** = true (если вычисляемый столбец сохраняется)  
  
-   **UserDataAccess** = false  
  
-   **SystemDataAccess** = false  
  
 Дополнительные сведения см. в разделе [Indexes on Computed Columns](../../relational-databases/indexes/indexes-on-computed-columns.md).  
  
### <a name="calling-extended-stored-procedures-from-functions"></a>Вызов расширенной хранимой процедуры из функций  
 Расширенные хранимые процедуры, если они вызываются из тела функции, не могут возвращать клиенту результирующие наборы. Все API ODS, которые возвращают результирующие наборы клиенту, вернут FAIL. Расширенная хранимая процедура может подключаться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но она не должна пытаться присоединиться к той же транзакции, что и функция, из которой вызвана расширенная хранимая процедура.  
  
 Как и при вызове из пакета или хранимой процедуры, расширенная хранимая процедура будет выполняться в контексте учетной записи системы безопасности Windows, от имени которой выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Владелец хранимой процедуры должен это понимать, когда он предоставляет пользователям разрешение EXECUTE на нее.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Определяемые пользователем функции не могут выполнять действия, изменяющие состояние базы данных.  
  
 Определяемые пользователем функции не могут содержать предложение OUTPUT INTO, целью которого является таблица.  
  
 Следующие инструкции компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] не могут быть включены в определение определяемой пользователем функции [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
-   BEGIN DIALOG CONVERSATION  
  
-   END CONVERSATION  
  
-   GET CONVERSATION GROUP  
  
-   MOVE CONVERSATION  
  
-   RECEIVE  
  
-   SEND  
  
 Определяемые пользователем функции могут быть вложенными, то есть из одной функции может быть вызвана другая. Уровень вложенности увеличивается на единицу каждый раз, когда начинается выполнение вызванной функции и уменьшается на единицу, когда ее выполнение завершается. Вложенность определяемых пользователем функций не может превышать 32 уровней. Превышение максимального уровня вложенности приводит к ошибке выполнения для всей цепочки вызываемых функций. Каждый вызов управляемого кода из определяемой пользователем функции [!INCLUDE[tsql](../../includes/tsql-md.md)] считается за один уровень вложенности из 32 возможных. Методы, вызываемые из управляемого кода, под это ограничение не подпадают.  
  
### <a name="using-sort-order-in-clr-table-valued-functions"></a>Использование порядка сортировки в функциях CLR с табличным значением  
 При использовании предложения ORDER в функциях CLR с табличным значением придерживайтесь следующих рекомендаций.  
  
-   Необходимо гарантировать, чтобы результаты всегда были упорядочены в указанном порядке. Если результаты находятся не в указанном порядке, при выполнении запроса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сформирует сообщение об ошибке.  
  
-   Если указано предложение ORDER, выходные данные функции с табличным значением должны быть отсортированы в соответствии с параметрами сортировки столбца (явными или неявными). Например, если для столбца используются параметры сортировки для китайского языка (указанные в определении функции с табличным значением или полученные из параметров сортировки базы данных), то возвращаемые результаты должны быть отсортированы в соответствии с правилами сортировки, принятыми в китайском языке.  
  
-   При использовании предложение ORDER всегда проверяется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при возврате результатов, независимо от его использования обработчиком запросов для выполнения оптимизации. Рекомендуется использовать предложение ORDER только при уверенности в его пользе для обработчика запросов.  
  
-   Обработчик запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически использует преимущества предложения ORDER в следующих случаях.  
  
    -   Запросы Insert, в которых предложение ORDER совместимо с индексом.  
  
    -   Предложения ORDER BY, совместимые с предложением ORDER.  
  
    -   Статистические выражения, в которых предложения GROUP BY и ORDER совместимы.  
  
    -   Статистические выражения с ключевым словом DISTINCT, в которых уникальные столбцы совместимы с предложением ORDER.  
  
 Предложение ORDER не гарантирует упорядочивания результатов при выполнении запроса SELECT, если оно не указано в самом запросе. В разделе [sys.function_order_columns &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-function-order-columns-transact-sql.md) сведения о том, как запрос столбцов, включенных в порядке сортировки для функций, возвращающих табличные значения.  
  
## <a name="metadata"></a>Метаданные  
 В следующей таблице приводятся системные представления каталога, возвращающие метаданные об определяемых пользователем функциях.  
  
|Системное представление|Description|  
|-----------------|-----------------|  
|[sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)|См. пример E в подразделе «примеры» ниже.|  
|[sys.assembly_modules](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)|Выводит сведения об определяемых пользователем функциях CLR.|  
|[sys.parameters](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)|Выводит сведения о параметрах, определенных в определяемых пользователем функциях.|  
|[sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)|Отображает базовые объекты, на которые ссылается функция.|  
  
## <a name="permissions"></a>Permissions  
 Требуется разрешение CREATE FUNCTION на базу данных и разрешение ALTER на схему, в которой создается функция. Если в функции указан определяемый пользователем тип, требуется разрешение EXECUTE на этот тип.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-a-scalar-valued-user-defined-function-that-calculates-the-iso-week"></a>A. Применение скалярной определяемой пользователем функции, вычисляющей неделю по ISO  
 В следующем примере показано создание определяемой пользовательской функции `ISOweek`, которая получает в качестве аргумента дату и вычисляет номер недели по ISO. Для правильной работы этой функции перед ее вызовом должна быть выполнена инструкция `SET DATEFIRST 1`.  
  
 В примере также показано использование [EXECUTE AS](../../t-sql/statements/execute-as-clause-transact-sql.md) предложений, чтобы указать контекст безопасности, в котором может быть выполнена хранимая процедура. В этом примере параметр `CALLER` указывает, что процедура будет выполнена в контексте пользователя, который ее вызывает. Другие параметры, можно указать, SELF, OWNER и *имя_пользователя*.  
  
 Показан вызов функции. Обратите внимание, что `DATEFIRST` устанавливается в значение `1`.  
  
```tsql
CREATE FUNCTION dbo.ISOweek (@DATE datetime)  
RETURNS int  
WITH EXECUTE AS CALLER  
AS  
BEGIN  
     DECLARE @ISOweek int;  
     SET @ISOweek= DATEPART(wk,@DATE)+1  
          -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104');  
--Special cases: Jan 1-3 may belong to the previous year  
     IF (@ISOweek=0)   
          SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1   
               AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1;  
--Special case: Dec 29-31 may belong to the next year  
     IF ((DATEPART(mm,@DATE)=12) AND   
          ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28))  
          SET @ISOweek=1;  
     RETURN(@ISOweek);  
END;  
GO  
SET DATEFIRST 1;  
SELECT dbo.ISOweek(CONVERT(DATETIME,'12/26/2004',101)) AS 'ISO Week';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
``` 
ISO Week  
----------------  
52  
```  
  
### <a name="b-creating-an-inline-table-valued-function"></a>Б. Создание встроенной функции с табличным значением  
 Результатом следующего примера является встроенная функция, возвращающая табличное значение в базу данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Он возвращает три столбца `ProductID`, `Name` и статистическое вычисление итоговых значений с начала года по магазину — `YTD Total` для каждого продукта, проданных в магазине.  
  
```tsql  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
GO  
```

 При вызове этой функции выполняется следующий запрос.    

```tsql  
SELECT * FROM Sales.ufn_SalesByStore (602);  
```  
  
### <a name="c-creating-a-multi-statement-table-valued-function"></a>В. Создание функции с табличным значением из нескольких инструкций  
 В следующем примере создается функция с табличным значением `fn_FindReports(InEmpID)` в базе данных AdventureWorks2012. Если ей передать допустимый идентификатор сотрудника, она вернет таблицу, в которой содержатся все сотрудники, которые прямо или опосредованно перед ним отчитываются. В функции для построения иерархического списка сотрудников используется рекурсивное обобщенное табличное выражение (CTE). Дополнительные сведения о рекурсивных обобщенных табличных выражений см. в разделе [с общее_табличное_выражение &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
```tsql  
CREATE FUNCTION dbo.ufn_FindReports (@InEmpID INTEGER)  
RETURNS @retFindReports TABLE   
(  
    EmployeeID int primary key NOT NULL,  
    FirstName nvarchar(255) NOT NULL,  
    LastName nvarchar(255) NOT NULL,  
    JobTitle nvarchar(50) NOT NULL,  
    RecursionLevel int NOT NULL  
)  
--Returns a result set that lists all the employees who report to the   
--specific employee directly or indirectly.*/  
AS  
BEGIN  
WITH EMP_cte(EmployeeID, OrganizationNode, FirstName, LastName, JobTitle, RecursionLevel) -- CTE name and columns  
    AS (  
        -- Get the initial list of Employees for Manager n
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, 0   
        FROM HumanResources.Employee e   
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        WHERE e.BusinessEntityID = @InEmpID  
        UNION ALL  
        -- Join recursive member to anchor
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, RecursionLevel + 1   
        FROM HumanResources.Employee e   
            INNER JOIN EMP_cte  
            ON e.OrganizationNode.GetAncestor(1) = EMP_cte.OrganizationNode  
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        )  
-- copy the required columns to the result of the function   
   INSERT @retFindReports  
   SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
   FROM EMP_cte   
   RETURN  
END;  
GO  
-- Example invocation  
SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
FROM dbo.ufn_FindReports(1);   
  
GO  
```  
  
### <a name="d-creating-a-clr-function"></a>Г. Создание функции CLR  
 В примере создается функция CLR `len_s`. Перед ее созданием сборка `SurrogateStringFunction.dll` регистрируется в локальной базе данных.  
  
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```tsql  
DECLARE @SamplesPath nvarchar(1024);  
-- You may have to modify the value of this variable if you have  
-- installed the sample in a location other than the default location.  
SELECT @SamplesPath = REPLACE(physical_name, 'Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\master.mdf', 
                                              'Microsoft SQL Server\130\Samples\Engine\Programmability\CLR\')   
    FROM master.sys.database_files   
    WHERE name = 'master';  
  
CREATE ASSEMBLY [SurrogateStringFunction]  
FROM @SamplesPath + 'StringManipulate\CS\StringManipulate\bin\debug\SurrogateStringFunction.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
GO  
  
CREATE FUNCTION [dbo].[len_s] (@str nvarchar(4000))  
RETURNS bigint  
AS EXTERNAL NAME [SurrogateStringFunction].[Microsoft.Samples.SqlServer.SurrogateStringFunction].[LenS];  
GO  
```  
  
 Пример создания табличной функции CLR см. в разделе [CLR Table-Valued функции](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-table-valued-functions.md).  
  
### <a name="e-displaying-the-definition-of-includetsqlincludestsql-mdmd-user-defined-functions"></a>Д. Отображение определения [!INCLUDE[tsql](../../includes/tsql-md.md)] определяемых пользователем функций  
  
```tsql  
SELECT definition, type   
FROM sys.sql_modules AS m  
JOIN sys.objects AS o ON m.object_id = o.object_id   
    AND type IN ('FN', 'IF', 'TF');  
GO  
```  
  
 Определения зашифрованных функций, созданных с помощью параметра ENCRYPTION, в sys.sql_modules не отображаются, но все остальные сведения о них доступны.  
  
## <a name="see-also"></a>См. также:  
 [ALTER FUNCTION (Transact-SQL)](../../t-sql/statements/alter-function-transact-sql.md)   
 [ФУНКЦИЯ СБРОСА &#40; Transact-SQL &#41;](../../t-sql/statements/drop-function-transact-sql.md)   
 [OBJECTPROPERTYEX &#40; Transact-SQL &#41;](../../t-sql/functions/objectpropertyex-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.assembly_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)   
 [Определяемые пользователем функции CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [СОЗДАТЬ ПОЛИТИКУ безопасности &#40; Transact-SQL &#41;](../../t-sql/statements/create-security-policy-transact-sql.md)  
  
 


