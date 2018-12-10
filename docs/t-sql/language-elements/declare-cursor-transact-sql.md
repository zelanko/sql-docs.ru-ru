---
title: DECLARE CURSOR (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DECLARE_CURSOR_TSQL
- CURSOR_TSQL
- DECLARE CURSOR
- CURSOR
dev_langs:
- TSQL
helpviewer_keywords:
- DECLARE CURSOR statement
- cursors [SQL Server], attributes
- local cursors [SQL Server]
- nesting cursors
- Transact-SQL cursors, attributes
- global cursors [SQL Server]
ms.assetid: 5a3a27aa-03e8-4c98-a27e-809282379b21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e085aff8a426a748e49c450e1bbb6258881583e5
ms.sourcegitcommit: f1cf91e679d1121d7f1ef66717b173c22430cb42
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/29/2018
ms.locfileid: "52586307"
---
# <a name="declare-cursor-transact-sql"></a>DECLARE CURSOR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Определяет такие атрибуты серверного курсора языка [!INCLUDE[tsql](../../includes/tsql-md.md)], как свойства просмотра и запрос, используемый для построения результирующего набора, на котором работает курсор. Инструкция `DECLARE CURSOR` поддерживает как синтаксис стандарта ISO, так и синтаксис, использующий набор расширений языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ISO Syntax  
DECLARE cursor_name [ INSENSITIVE ] [ SCROLL ] CURSOR   
     FOR select_statement   
     [ FOR { READ ONLY | UPDATE [ OF column_name [ ,...n ] ] } ]  
[;]  
Transact-SQL Extended Syntax  
DECLARE cursor_name CURSOR [ LOCAL | GLOBAL ]   
     [ FORWARD_ONLY | SCROLL ]   
     [ STATIC | KEYSET | DYNAMIC | FAST_FORWARD ]   
     [ READ_ONLY | SCROLL_LOCKS | OPTIMISTIC ]   
     [ TYPE_WARNING ]   
     FOR select_statement   
     [ FOR UPDATE [ OF column_name [ ,...n ] ] ]  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *cursor_name*  
 Имя определенного серверного курсора [!INCLUDE[tsql](../../includes/tsql-md.md)]. Аргумент *cursor_name* должен соответствовать требованиям, предъявляемым к идентификаторам.  
  
 INSENSITIVE  
 Определяет курсор, который создает временную копию данных для использования курсором. Все запросы к курсору обращаются к указанной временной таблице в базе данных **tempdb**, поэтому изменения базовых таблиц не влияют на данные, возвращаемые выборками для данного курсора, а сам курсор не позволяет производить изменения. Если при использовании синтаксиса ISO не указан параметр `INSENSITIVE`, зафиксированные обновления и удаления, сделанные в базовых таблицах, отображаются в последующих выборках.  
  
 SCROLL  
 Указывает, что доступны все параметры выборки (`FIRST`, `LAST`, `PRIOR`, `NEXT`, `RELATIVE`, `ABSOLUTE`). Если в инструкции `DECLARE CURSOR` стандарта ISO не указан параметр `SCROLL`, то поддерживается только параметр выборки `NEXT`. Если указан аргумент `FAST_FORWARD`, задать `SCROLL` невозможно.  
  
 *select_statement*  
 Стандартная инструкция `SELECT`, которая определяет результирующий набор курсора. Ключевые слова `FOR BROWSE` и `INTO` недопустимы в аргументе *select_statement*, входящем в объявление курсора.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] неявным образом преобразует курсор в другой тип, если предложения в аргументе *select_statement* вызывают конфликт с функциями курсора запрошенного типа.  
  
 READ ONLY  
 Предотвращает изменения, сделанные через этот курсор. На курсов нельзя ссылаться в приложении `WHERE CURRENT OF` в инструкции `UPDATE` или `DELETE`. Этот параметр имеет преимущество над установленной по умолчанию возможностью обновления курсора.  
  
 UPDATE [OF *column_name* [**,**...*n*]]  
 Определяет обновляемые столбцы в курсоре. Если OF <column_name> [, <... n>] указан, вносить изменения можно только в перечисленные столбцы. Если инструкция `UPDATE` используется без списка столбцов, то обновление возможно для всех столбцов.  
  
 *cursor_name*  
 Имя определенного серверного курсора [!INCLUDE[tsql](../../includes/tsql-md.md)]. Аргумент *cursor_name* должен соответствовать требованиям, предъявляемым к идентификаторам.  
  
 LOCAL  
 Указывает, что курсор является локальным по отношению к пакету, хранимой процедуре или триггеру, в котором он был создан. Имя курсора допустимо только внутри этой области. На курсор могут ссылаться локальные переменные пакета, хранимые процедуры, триггеры или выходной параметр `OUTPUT` хранимой процедуры. Параметр `OUTPUT` используется для передачи локального курсора вызывающему его пакету, хранимой процедуре или триггеру, который затем может присвоить параметр переменной курсора с целью последующего обращения к курсору после завершения хранимой процедуры. Курсор неявно освобождается после завершения выполнения пакета, хранимой процедуры или триггера, за исключением случая, когда курсор был передан параметру `OUTPUT`. Если курсор был передан параметру `OUTPUT`, то курсор освобождается при освобождении всех ссылающихся на него переменных или при выходе из области видимости.  
  
 GLOBAL  
 Указывает, что курсор является глобальным по отношению к соединению. Имя курсора может использоваться любой хранимой процедурой или пакетом, которые выполняются в соединении. Курсор неявно освобождается только в случае разрыва соединения.  
  
> [!NOTE]  
>  Если не указан ни один из параметров `GLOBAL` или `LOCAL`, то значение по умолчанию управляется параметром **default to local cursor** базы данных.  
  
 FORWARD_ONLY  
 Указывает, что курсор может просматриваться только от первой строки к последней. Поддерживается только параметр выборки `FETCH NEXT`. Если параметр `FORWARD_ONLY` указан без ключевых слов `STATIC`, `KEYSET` или `DYNAMIC`, курсор работает как курсор DYNAMIC. Если не указан ни один из параметров `FORWARD_ONLY` или `SCROLL`, по умолчанию используется `FORWARD_ONLY`, пока не будут заданы ключевые слова `STATIC`, `KEYSET` или `DYNAMIC`. Курсоры `STATIC`, `KEYSET` и `DYNAMIC` по умолчанию получают значение `SCROLL`. В отличие от API-интерфейсов базы данных, таких как ODBC и ADO, `FORWARD_ONLY` поддерживается с курсорами `STATIC`, `KEYSET`, и `DYNAMIC` [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 STATIC  
 Определяет курсор, который создает временную копию данных для использования курсором. Все запросы к курсору обращаются к указанной временной таблице в базе данных **tempdb**, поэтому изменения базовых таблиц не влияют на данные, возвращаемые выборками для данного курсора, а сам курсор не позволяет производить изменения.  
  
 KEYSET  
 Указывает, что членство или порядок строк в курсоре неизменны при его открытии. Набор ключей, однозначно определяющих строки, встроен в таблицу в базе данных **tempdb** с именем **keyset**.  
  
> [!NOTE]  
> Если запрос ссылается хотя бы на одну таблицу, не имеющую уникального индекса, курсор keyset преобразуется в статический курсор.  
  
 Изменения неключевых значений в базовых таблицах, сделанные владельцем курсора или зафиксированные другими пользователями, отображаются при просмотре курсора владельцем. Вставки, сделанные другими пользователями, не отображаются (вставки не могут быть сделаны с помощью серверного курсора языка [!INCLUDE[tsql](../../includes/tsql-md.md)]). Если какая-то строка удаляется, при попытке выбрать эту строку функция `@@FETCH_STATUS` возвращает значение –2. Обновления значений ключа из-за границ курсора аналогично удалению старой строки с последующей вставкой новой строки. Строка с новыми значениями невидима, и при попытке извлечь строку со старыми значениями функция `@@FETCH_STATUS` возвращает значение –2. Обновления видимы сразу, если они сделаны через курсор с помощью предложения `WHERE CURRENT OF`.  
  
 DYNAMIC  
 Определяет курсор, отображающий все изменения данных, сделанные в строках результирующего набора при просмотре этого курсора. Значения данных, порядок и членство строк в каждой выборке могут меняться. Параметр выборки ABSOLUTE динамическими курсорами не поддерживается.  
  
 FAST_FORWARD  
 Указывает курсор `FORWARD_ONLY`, `READ_ONLY`, для которого включена оптимизация производительности. Если указан `SCROLL` или `FOR_UPDATE`, задать `FAST_FORWARD` невозможно.  
  
> [!NOTE]  
>  `FAST_FORWARD` и `FORWARD_ONLY` можно использовать в одной инструкции `DECLARE CURSOR`.  
  
 READ_ONLY  
 Предотвращает изменения, сделанные через этот курсор. На курсов нельзя ссылаться в приложении `WHERE CURRENT OF` в инструкции `UPDATE` или `DELETE`. Этот параметр имеет преимущество над установленной по умолчанию возможностью обновления курсора.  
  
 SCROLL_LOCKS  
 Указывает, что позиционированные обновления или удаления, осуществляемые с помощью курсора, гарантированно будут выполнены успешно. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] блокирует строки по мере их считывания в курсор для обеспечения доступности этих строк для последующих изменений. Если указан `FAST_FORWARD` или `STATIC`, задать `SCROLL_LOCKS` невозможно.  
  
 OPTIMISTIC  
 Указывает, что позиционированные обновления или удаления, осуществляемые с помощью курсора, не будут выполнены, если с момента считывания в курсор строка была обновлена. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не блокирует строки по мере их считывания в курсор. Вместо этого используются сравнения значений столбца **timestamp** или значений контрольных сумм, если в таблице нет столбца **timestamp**, для определения факта изменения строки после ее считывания в курсор. Если строка была изменена, то попытки позиционированного обновления или удаления будут безрезультатными. Если указан аргумент `FAST_FORWARD`, задать `OPTIMISTIC` невозможно.  
  
 TYPE_WARNING  
 Указывает, что клиенту будет отправлено предупреждение, если курсор неявно будет преобразован из одного запрашиваемого типа в другой.  
  
 *select_statement*  
 Стандартная инструкция SELECT, которая определяет результирующий набор курсора. Ключевые слова `COMPUTE`, `COMPUTE BY`, `FOR BROWSE` и `INTO` недопустимы в аргументе *select_statement*, входящем в объявление курсора.  
  
> [!NOTE]  
>  В объявлении курсора можно использовать указание запроса, но если используется предложение `FOR UPDATE OF`, то после `FOR UPDATE OF` следует указать параметр `OPTION (<query_hint>)`.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] неявным образом преобразует курсор в другой тип, если предложения в аргументе *select_statement* вызывают конфликт с функциями курсора запрошенного типа. Дополнительные сведения см. в разделе "Неявные преобразования курсора".  
  
 FOR UPDATE [OF *column_name* [**,**...*n*]]  
 Определяет обновляемые столбцы в курсоре. Если `OF <column_name> [, <... n>]` определено, только перечисленные столбцы позволяют вносить изменения. Если инструкция `UPDATE` используется без списка столбцов, то обновление возможно для всех столбцов, за исключением случая, когда был указан параметр параллелизма `READ_ONLY`.  
  
## <a name="remarks"></a>Remarks  
`DECLARE CURSOR` определяет такие атрибуты серверного курсора языка [!INCLUDE[tsql](../../includes/tsql-md.md)], как свойства просмотра и запрос, используемый для построения результирующего набора, на котором работает курсор. Инструкция `OPEN` заполняет результирующий набор, а оператор `FETCH` возвращает из него строку. Инструкция `CLOSE` очищает текущий результирующий набор, связанный с курсором. Инструкция `DEALLOCATE` освобождает ресурсы, используемые курсором.  
  
 Первая форма инструкции `DECLARE CURSOR` использует синтаксис ISO для задания параметров работы курсора. Вторая форма инструкции `DECLARE CURSOR` использует расширения языка [!INCLUDE[tsql](../../includes/tsql-md.md)], позволяющие определять курсоры с помощью таких же типов, как типы, используемые в курсорных функциях API баз данных, таких как ODBC и ADO.  
  
 Нельзя смешивать две эти формы. Если вы определяете ключевые слова `SCROLL` или `INSENSITIVE` до ключевого слова `CURSOR`, вы не сможете использовать никакие ключевые слова между ключевыми словами `CURSOR` и `FOR <select_statement>`. Если вы указываете ключевые слова между ключевыми словами `CURSOR` и `FOR <select_statement>`, вы не сможете задать `SCROLL` или `INSENSITIVE` перед ключевым словом `CURSOR`.  
  
 Если `DECLARE CURSOR` с помощью синтаксиса [!INCLUDE[tsql](../../includes/tsql-md.md)] не указывает `READ_ONLY`, `OPTIMISTIC` или `SCROLL_LOCKS`, значение по умолчанию выглядит следующим образом:  
  
-   Если инструкция `SELECT` не поддерживает обновления (или недостаточно разрешений, или при доступе к удаленным таблицам, не поддерживающим обновление, и т. п.), то курсору присваивается параметр `READ_ONLY`.  
  
-   Курсоры `STATIC` и `FAST_FORWARD` по умолчанию получают значение `READ_ONLY`.  
  
-   Курсоры `DYNAMIC` и `KEYSET` по умолчанию получают значение `OPTIMISTIC`.  
  
 Ссылки на курсоры могут производиться только другими инструкциями языка [!INCLUDE[tsql](../../includes/tsql-md.md)]. Функции API баз данных не могут ссылаться на курсоры. Например, после объявления курсора функции и методы OLE DB, ODBC или ADO не могут ссылаться на его имя. Строки курсора не могут быть выбраны с помощью соответствующих функций и методов API; для этой цели необходимо использовать инструкции FETCH языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Приведенные ниже хранимые процедуры могут быть использованы для определения свойств курсора после его объявления.  
  
|Системные хранимые процедуры|Описание|  
|------------------------------|-----------------|  
|**sp_cursor_list**|Возвращает список курсоров, доступных для соединения в настоящий момент времени, а также их атрибуты.|  
|**sp_describe_cursor**|Описывает атрибуты курсора, например имеет ли он тип "forward-only" или "scrolling".|  
|**sp_describe_cursor_columns**|Описывает атрибуты столбцов результирующего набора.|  
|**sp_describe_cursor_tables**|Описывает базовые таблицы, к которым курсор получает доступ.|  
  
 Переменные могут использоваться в качестве составных частей выражения *select_statement*, объявляющего курсор. Значения переменных курсора после его объявления не изменяются.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения `DECLARE CURSOR`предоставляются всем пользователям, имеющим разрешения `SELECT` для используемых курсором представлений, таблиц и столбцов.
 
## <a name="limitations-and-restrictions"></a>Ограничения

Нельзя использовать курсоры или триггеры в таблице с кластеризованным индексом columnstore. Это ограничение не применяется к некластеризованным индексам columnstore. Курсоры и триггеры можно использовать в таблице с некластеризованным индексом columnstore. 
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-simple-cursor-and-syntax"></a>A. Использование простого курсора и синтаксиса  

Результирующий набор, создаваемый при открытии данного курсора, включает в себя все строки и столбцы таблицы. Этот курсор можно обновлять, все обновления и удаления представлены в выборке для этого курсора. `FETCH NEXT` является единственно доступной выборкой, так как параметр `SCROLL` не был определен.  
 
```sql  
DECLARE vend_cursor CURSOR  
    FOR SELECT * FROM Purchasing.Vendor  
OPEN vend_cursor  
FETCH NEXT FROM vend_cursor;  
```  
  
### <a name="b-using-nested-cursors-to-produce-report-output"></a>Б. Использование вложенных курсоров для вывода отчета  
 В следующем примере вложенные курсоры используются для вывода сложного отчета. Для каждого поставщика объявляется внутренний курсор.  
  
```sql  
SET NOCOUNT ON;  
  
DECLARE @vendor_id int, @vendor_name nvarchar(50),  
    @message varchar(80), @product nvarchar(50);  
  
PRINT '-------- Vendor Products Report --------';  
  
DECLARE vendor_cursor CURSOR FOR   
SELECT VendorID, Name  
FROM Purchasing.Vendor  
WHERE PreferredVendorStatus = 1  
ORDER BY VendorID;  
  
OPEN vendor_cursor  
  
FETCH NEXT FROM vendor_cursor   
INTO @vendor_id, @vendor_name  
  
WHILE @@FETCH_STATUS = 0  
BEGIN  
    PRINT ' '  
    SELECT @message = '----- Products From Vendor: ' +   
        @vendor_name  
  
    PRINT @message  
  
    -- Declare an inner cursor based     
    -- on vendor_id from the outer cursor.  
  
    DECLARE product_cursor CURSOR FOR   
    SELECT v.Name  
    FROM Purchasing.ProductVendor pv, Production.Product v  
    WHERE pv.ProductID = v.ProductID AND  
    pv.VendorID = @vendor_id  -- Variable value from the outer cursor  
  
    OPEN product_cursor  
    FETCH NEXT FROM product_cursor INTO @product  
  
    IF @@FETCH_STATUS <> 0   
        PRINT '         <<None>>'       
  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
  
        SELECT @message = '         ' + @product  
        PRINT @message  
        FETCH NEXT FROM product_cursor INTO @product  
        END  
  
    CLOSE product_cursor  
    DEALLOCATE product_cursor  
        -- Get the next vendor.  
    FETCH NEXT FROM vendor_cursor   
    INTO @vendor_id, @vendor_name  
END   
CLOSE vendor_cursor;  
DEALLOCATE vendor_cursor;  
```  
  
## <a name="see-also"></a>См. также  
 [@@FETCH_STATUS (Transact-SQL)](../../t-sql/functions/fetch-status-transact-sql.md)   
 [CLOSE (Transact-SQL)](../../t-sql/language-elements/close-transact-sql.md)   
 [Курсоры (Transact-SQL)](../../t-sql/language-elements/cursors-transact-sql.md)   
 [DEALLOCATE (Transact-SQL)](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [FETCH (Transact-SQL)](../../t-sql/language-elements/fetch-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
