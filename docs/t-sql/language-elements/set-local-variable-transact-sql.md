---
title: "ЗАДАТЬ @local_variable (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- SET @local_variable
- variables [SQL Server], assigning
- SET statement, @local_variable
- local variables [SQL Server]
ms.assetid: d410e06e-061b-4c25-9973-b2dc9b60bd85
caps.latest.revision: 52
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5a92fa424de70d1ba9cccf437a2de49ab8432ba1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-localvariable-transact-sql"></a>ЗАДАТЬ @local_variable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Задает указанный локальную переменную, предварительно созданную при помощи инструкции DECLARE @*local_variable* инструкции с указанным значением.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET   
{ @local_variable  
    [ . { property_name | field_name } ] = { expression | udt_name { . | :: } method_name }  
}  
|  
{ @SQLCLR_local_variable.mutator_method  
}  
|  
{ @local_variable  
    {+= | -= | *= | /= | %= | &= | ^= | |= } expression  
}  
|   
  { @cursor_variable =   
    { @cursor_variable | cursor_name   
    | { CURSOR [ FORWARD_ONLY | SCROLL ]   
        [ STATIC | KEYSET | DYNAMIC | FAST_FORWARD ]   
        [ READ_ONLY | SCROLL_LOCKS | OPTIMISTIC ]   
        [ TYPE_WARNING ]   
    FOR select_statement   
        [ FOR { READ ONLY | UPDATE [ OF column_name [ ,...n ] ] } ]   
      }   
    }  
}   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET @local_variable {+= | -= | *= | /= | %= | &= | ^= | |= } expression  
  
```  
  
## <a name="arguments"></a>Аргументы  
 **@***local_variable*  
 Имя переменной любого типа, за исключением **курсор**, **текст**, **ntext**, **изображения**, или **таблицы**. Имена переменных должны начинаться с одного символа (**@**). Имена переменных должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md).  
  
 *property_name*  
 Свойство определяемого пользователем типа.  
  
 *имя_поля*  
 Общее поле определяемого пользователем типа.  
  
 *udt_name*  
 Имя определяемого пользователем типа среды CLR.  
  
 { **.** | **::** }  
 Указывает метод пользовательского типа среды CLR. Для метода экземпляра (не статического) используйте точку (**.**). Для статического метода используйте два двоеточия (**::**). Для обращения к методу, свойству или полю определяемого пользователем типа среды CLR необходимо разрешение EXECUTE для этого типа.  
  
 *имя_метода* **(** *аргумент* [ **,**... *n* ] **)**  
 Метод определяемого пользователем типа, который принимает один или несколько аргументов для изменения состояния экземпляра типа. Статические методы должны быть общими.  
  
 **@***SQLCLR_local_variable*  
 Переменная, тип которой находится в сборке. Дополнительные сведения см. в статье [Основные понятия о программировании интеграции со средой CLR](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md).  
  
 *mutator_method*  
 Метод из сборки, который может менять состояние объекта. К этому методу будет применяться свойство SQLMethodAttribute.IsMutator.  
  
 { **+=** | **-=** | **\*=** | **/=** | **%=** | **&=** | **^=** | **|=** }  
 Составной оператор присваивания:  
  
 +=              Сложение и присваивание  
  
 -=               Вычитание и присваивание  
  
 *=              Умножение и присваивание  
  
 /=               Деление и присваивание  
  
 %=             Остаток от деления и присваивание  
  
 &=                     выполнить побитовое И и присвоить  
  
 =                     выполнить побитовое исключающее ИЛИ и присвоить  
  
 =                     выполнить побитовое ИЛИ и присвоить  
  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 *cursor_variable*  
 Имя переменной курсора. Если переменная целевого курсора ранее ссылалась на другой курсор, эта ссылка будет удалена.  
  
 *cursor_name*  
 Имя курсора, объявленного при помощи инструкции DECLARE CURSOR.  
  
 CURSOR  
 Указывает, что инструкция SET содержит декларацию курсора.  
  
 SCROLL  
 Указывает, что курсор поддерживает все параметры выборки: FIRST, LAST, NEXT, PRIOR, RELATIVE и ABSOLUTE. Аргумент SCROLL не может быть задан, если задан аргумент FAST_FORWARD.  
  
 FORWARD_ONLY  
 Указывает, что курсор поддерживает только параметр FETCH NEXT. Курсор может быть извлечен в одном направлении с первой до последней строки. Если аргумент FORWARD_ONLY задан без ключевых слов STATIC, KEYSET или DYNAMIC, создается курсор типа DYNAMIC. Если не указаны ни аргумент FORWARD_ONLY, ни аргумент SCROLL, по умолчанию используется аргумент FORWARD_ONLY, если нет ключевых слов STATIC, KEYSET или DYNAMIC. Для курсоров STATIC, KEYSET и DYNAMIC аргумент SCROLL добавляется по умолчанию.  
  
 STATIC  
 Определяет курсор, который создает временную копию данных для использования курсором. Ответы на все запросы к курсору берутся из временной таблицы в базе данных tempdb, поэтому изменения основных таблиц не отражаются в возвращенных выборками этого курсора данными и курсор не позволяет производить изменения.  
  
 KEYSET  
 Указывает, что членство или порядок строк в курсоре неизменны при его открытии. Набор ключей, который уникально определяет строки, встроен в keysettable в базе данных tempdb. Изменения на неключевые значения в базовых таблицах, либо созданных владельцем курсора, либо зафиксированных другими пользователям, видны при прокрутке владельцем курсора содержимого курсора. Вставки, выполненные другими пользователями, не будут видны, и невозможно выполнить вставку через серверный курсор [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Если удаляется строка, попытка выборки строк возвращает @@FETCH_STATUS -2. Обновления значений ключа из-за границ курсора аналогично удалению старой строки с последующей вставкой новой строки. Строка с новыми значениями невидима, и попытки выборки строки со старыми значениями возвращают @@FETCH_STATUS -2. Обновления видимы сразу, если они сделаны через курсор с помощью предложения WHERE CURRENT OF.  
  
 DYNAMIC  
 Определяет курсор, который отражает все изменения данных в строках в его результирующем наборе по мере того, как владелец курсора осуществляет прокрутку по курсору. Значения данных, порядок и членство строк в каждой выборке могут меняться. Параметры абсолютной и относительной выборки не поддерживаются динамическими курсорами.  
  
 FAST_FORWARD  
 Задает курсор типа FORWARD_ONLY, READ_ONLY с включенной оптимизацией. Аргумент FAST_FORWARD не может быть задан, если задан аргумент SCROLL.  
  
 READ_ONLY  
 Предотвращает внесение изменений через этот курсор. Предложение WHERE CURRENT OF не может иметь ссылку на курсор в инструкции UPDATE или DELETE. Этот параметр имеет преимущество над установленной по умолчанию возможностью обновления курсора.  
  
 SCROLL LOCKS  
 Указывает, что позиционированные обновления или удаления, осуществляемые с помощью курсора, гарантированно будут выполнены успешно. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] блокирует строки по мере их считывания в курсор, чтобы обеспечить доступность этих строк для последующих изменений. Аргумент SCROLL_LOCKS не может быть задан, если задан аргумент FAST_FORWARD.  
  
 OPTIMISTIC  
 Указывает, что позиционированные обновления или удаления, осуществляемые с помощью курсора, не будут выполнены, если с момента считывания в курсор строка была обновлена. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не блокирует строки по мере их считывания в курсор. Вместо этого используются сравнения значений столбца timestamp или значений контрольных сумм, если в таблице нет столбца timestamp, для определения факта изменения строки после ее считывания в курсор. Если строка была изменена, то попытки позиционированного обновления или удаления будут безрезультатными. Аргумент OPTIMISTIC не может быть задан, если задан аргумент FAST_FORWARD.  
  
 TYPE_WARNING  
 Указывает, что клиенту будет отправлено предупреждение, если курсор неявно будет преобразован из одного запрашиваемого типа в другой.  
  
 ДЛЯ *select_statement*  
 Стандартная инструкция SELECT, которая определяет результирующий набор курсора. Ключевые слова FOR BROWSE и INTO недопустимы в *select_statement* объявление курсора.  
  
 Если используются DISTINCT, UNION, GROUP BY или HAVING или статистическое выражение входит в *select_list*, курсор создается как СТАТИЧЕСКИЙ.  
  
 Если каждая из базовых таблиц не имеет уникального индекса и курсора ISO SCROLL или запрашивается курсор [!INCLUDE[tsql](../../includes/tsql-md.md)] KEYSET, он автоматически будет курсором STATIC.  
  
 Если *select_statement* содержит предложение ORDER BY, в котором столбцы не являются уникальными идентификаторами строк, курсор DYNAMIC будет преобразован в курсор KEYSET или в СТАТИЧЕСКИЙ курсор, если курсор KEYSET не может быть открыт. Тоже самое происходит с курсором, определенным при помощи синтаксиса ISO, но без ключевого слова STATIC.  
  
 READ ONLY  
 Предотвращает внесение изменений через этот курсор. Предложение WHERE CURRENT OF не может иметь ссылку на курсор в инструкции UPDATE или DELETE. Этот параметр имеет преимущество над установленной по умолчанию возможностью обновления курсора. Это ключевое слово отличается от READ_ONLY тем, что между READ и ONLY вместо подчеркивания употребляется пробел.  
  
 Обновление [OF *column_name*[ **,**... *n* ] ]  
 Определяет обновляемые столбцы в курсоре. Если OF *column_name* [**,**...  *n* ] определено, только перечисленные столбцы будут позволяют вносить изменения. Если список не предоставляется, все столбцы могут быть обновлены, если только курсор не был определен как READ_ONLY.  
  
## <a name="remarks"></a>Замечания  
 После объявления переменной она получает значение NULL. Используйте инструкцию SET, чтобы назначить значение, отличное от NULL, объявленной переменной. Инструкция SET, которая назначает значение переменной, возвращает одно значение. Если инициализируется несколько переменных, следует использовать отдельные инструкции SET для каждой локальной переменной.  
  
 Переменные могут быть использованы только в выражениях, но не вместо имен объектов или ключевых слов. Для создания динамических инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] используйте инструкцию EXECUTE.  
  
 Синтаксические правила для SET  **@**  *cursor_variable* не включают ключевые слова LOCAL и GLOBAL. При НАБОРЕ  **@**  *cursor_variable* = CURSOR... используется синтаксис, курсор создается как GLOBAL или LOCAL, в зависимости от настройки по умолчанию параметра локального курсора базы данных.  
  
 Переменные курсора всегда локальные, даже если ссылаются на глобальный курсор. Если переменная курсора ссылается на глобальный курсор, курсор имеет ссылки как на глобальный, так и на локальный курсоры. Дополнительные сведения см. в примере В.  
  
 Дополнительные сведения см. в разделе [DECLARE CURSOR &#40; Transact-SQL &#41; ](../../t-sql/language-elements/declare-cursor-transact-sql.md).  
  
 Составной оператор присваивания может использоваться везде, где выполняется присваивание с выражением справа от оператора, включающим переменные, или имеется инструкция SET в инструкциях UPDATE, SELECT и RECEIVE.  
  
 Не используйте переменную в инструкции SELECT для сцепления значений (то есть для вычисления статистических значений). Запрос может вернуть непредвиденные результаты. Это связано с тем, что все выражения в списке SELECT (включая назначения) могут быть выполнены не ровно один раз для каждой строки вывода. Дополнительные сведения см. в разделе [данной статьи БАЗЫ знаний](http://support.microsoft.com/kb/287515).  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в роли public. Все пользователи могут использовать НАБОР  **@**  *local_variable*.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-printing-the-value-of-a-variable-initialized-by-using-set"></a>A. Отображение значения переменной, инициализированной при помощи инструкции SET  
 В следующем примере создается `@myvar` переменной, возвращает строковое значение в переменную и выводятся на печать значения `@myvar` переменной.  
  
```  
DECLARE @myvar char(20);  
SET @myvar = 'This is a test';  
SELECT @myvar;  
GO  
```  
  
### <a name="b-using-a-local-variable-assigned-a-value-by-using-set-in-a-select-statement"></a>Б. Использование локальной переменной, значение которой назначено при помощи инструкции SET в инструкции SELECT  
 Следующий пример создает локальную переменную с именем `@state` и использует ее в инструкции `SELECT` для нахождения имен и фамилий всех работников, которые живут в штате `Oregon`.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @state char(25);  
SET @state = N'Oregon';  
SELECT RTRIM(FirstName) + ' ' + RTRIM(LastName) AS Name, City  
FROM HumanResources.vEmployee  
WHERE StateProvinceName = @state;  
```  
  
### <a name="c-using-a-compound-assignment-for-a-local-variable"></a>В. Использование составного оператора присваивания для локальной переменной  
 Следующие два примера позволяют получить один и тот же результат. Они создают локальную переменную с именем `@NewBalance`, умножают ее на 10 и отображают новое значение локальной переменной в инструкции `SELECT`. Во втором примере используется составной оператор присваивания.  
  
```  
/* Example one */  
DECLARE  @NewBalance  int ;  
SET  @NewBalance  =  10;  
SET  @NewBalance  =  @NewBalance  *  10;  
SELECT  @NewBalance;  
  
/* Example Two */  
DECLARE @NewBalance int = 10;  
SET @NewBalance *= 10;  
SELECT @NewBalance;  
```  
  
### <a name="d-using-set-with-a-global-cursor"></a>Г. Использование инструкции SET с глобальным курсором  
 Следующий пример создает локальную переменную и устанавливает переменную курсора в значение имени глобального курсора.  
  
```  
DECLARE my_cursor CURSOR GLOBAL   
FOR SELECT * FROM Purchasing.ShipMethod  
DECLARE @my_variable CURSOR ;  
SET @my_variable = my_cursor ;   
--There is a GLOBAL cursor declared(my_cursor) and a LOCAL variable  
--(@my_variable) set to the my_cursor cursor.  
DEALLOCATE my_cursor;   
--There is now only a LOCAL variable reference  
--(@my_variable) to the my_cursor cursor.  
```  
  
### <a name="e-defining-a-cursor-by-using-set"></a>Д. Определение курсора при помощи инструкции SET  
 Следующий пример использует инструкцию `SET` для определения курсора.  
  
```  
DECLARE @CursorVar CURSOR;  
  
SET @CursorVar = CURSOR SCROLL DYNAMIC  
FOR  
SELECT LastName, FirstName  
FROM AdventureWorks2012.HumanResources.vEmployee  
WHERE LastName like 'B%';  
  
OPEN @CursorVar;  
  
FETCH NEXT FROM @CursorVar;  
WHILE @@FETCH_STATUS = 0  
BEGIN  
    FETCH NEXT FROM @CursorVar  
END;  
  
CLOSE @CursorVar;  
DEALLOCATE @CursorVar;  
```  
  
### <a name="f-assigning-a-value-from-a-query"></a>Е. Присваивание значения из запроса  
 Следующий пример использует запрос для присваивания значения переменной.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @rows int;  
SET @rows = (SELECT COUNT(*) FROM Sales.Customer);  
SELECT @rows;  
```  
  
### <a name="g-assigning-a-value-to-a-user-defined-type-variable-by-modifying-a-property-of-the-type"></a>Ж. Присваивание значения переменной определяемого пользователем типа путем изменения свойства типа  
 Следующий пример устанавливает значение для определяемого пользователем типа `Point` путем изменения значения свойства типа `X`.  
  
```  
DECLARE @p Point;  
SET @p.X = @p.X + 1.1;  
SELECT @p;  
GO  
```  
  
### <a name="h-assigning-a-value-to-a-user-defined-type-variable-by-invoking-a-method-of-the-type"></a>З. Присваивание значения переменной определяемого пользователем типа путем вызова метода типа  
 В следующем примере задается значение для определяемого пользователем типа **точки** путем вызова метода `SetXY` типа.  
  
```  
DECLARE @p Point;  
SET @p=point.SetXY(23.5, 23.5);  
```  
  
### <a name="i-creating-a-variable-for-a-clr-type-and-calling-a-mutator-method"></a>И. Создание переменной для типа CLR и вызов метода мутатора  
 В следующем примере создается переменная для типа `Point`, а затем выполняется метод мутатора в `Point`.  
  
```  
CREATE ASSEMBLY mytest from 'c:\test.dll' WITH PERMISSION_SET = SAFE  
CREATE TYPE Point EXTERNAL NAME mytest.Point  
GO  
DECLARE @p Point = CONVERT(Point, '')  
SET @p.SetXY(22, 23);  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="j-printing-the-value-of-a-variable-initialized-by-using-set"></a>К. Отображение значения переменной, инициализированной при помощи инструкции SET  
 В следующем примере создается `@myvar` переменной, возвращает строковое значение в переменную и выводятся на печать значения `@myvar` переменной.  
  
```  
DECLARE @myvar char(20);  
SET @myvar = 'This is a test';  
SELECT top 1 @myvar FROM sys.databases;  
  
```  
  
### <a name="k-using-a-local-variable-assigned-a-value-by-using-set-in-a-select-statement"></a>Л. Использование локальной переменной, значение которой назначено при помощи инструкции SET в инструкции SELECT  
 В следующем примере создается локальная переменная с именем `@dept` и использует ее в `SELECT` инструкцию, чтобы найти имена и фамилии всех сотрудников, работающих в `Marketing` отдела.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @dept char(25);  
SET @dept = N'Marketing';  
SELECT RTRIM(FirstName) + ' ' + RTRIM(LastName) AS Name  
FROM DimEmployee   
WHERE DepartmentName = @dept;  
```  
  
### <a name="l-using-a-compound-assignment-for-a-local-variable"></a>М. Использование составного оператора присваивания для локальной переменной  
 Следующие два примера позволяют получить один и тот же результат. Они создают локальную переменную с именем `@NewBalance`, умножают ее на `10` и отображают новое значение локальной переменной в инструкции `SELECT`. Во втором примере используется составной оператор присваивания.  
  
```  
/* Example one */  
DECLARE  @NewBalance  int ;  
SET  @NewBalance  =  10;  
SET  @NewBalance  =  @NewBalance  *  10;  
SELECT  TOP 1 @NewBalance FROM sys.tables;  
  
/* Example Two */  
DECLARE @NewBalance int = 10;  
SET @NewBalance *= 10;  
SELECT TOP 1 @NewBalance FROM sys.tables;  
```  
  
### <a name="m-assigning-a-value-from-a-query"></a>Н. Присваивание значения из запроса  
 Следующий пример использует запрос для присваивания значения переменной.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @rows int;  
SET @rows = (SELECT COUNT(*) FROM dbo.DimCustomer);  
SELECT TOP 1 @rows FROM sys.tables;  
```  
  
## <a name="see-also"></a>См. также:  
 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  


