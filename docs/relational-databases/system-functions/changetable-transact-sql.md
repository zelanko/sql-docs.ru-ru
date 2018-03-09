---
title: "CHANGETABLE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/08/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHANGETABLE_TSQL
- CHANGETABLE
dev_langs:
- TSQL
helpviewer_keywords:
- CHANGETABLE
- change tracking [SQL Server], CHANGETABLE
ms.assetid: d405fb8d-3b02-4327-8d45-f643df7f501a
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6fa552ec5c819773153118be3b45374570b5d6e2
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="changetable-transact-sql"></a>CHANGETABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает информацию отслеживания изменений для таблицы. Можно использовать эту инструкцию для возвращения всех изменений таблицы или информации отслеживания изменений для конкретной строки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CHANGETABLE (  
    { CHANGES table , last_sync_version  
    | VERSION table , <primary_key_values> } )  
[AS] table_alias [ ( column_alias [ ,...n ] )  
  
<primary_key_values> ::=  
( column_name [ , ...n ] ) , ( value [ , ...n ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 ИЗМЕНЕНИЯ *таблицы* , *last_sync_version*  
 Возвращает данные отслеживания изменений для всех изменений в таблицу, произведенных после версии, который задается параметром *last_sync_version*.  
  
 *table*  
 Пользовательская таблица, в которой регистрируются отслеживаемые изменения. Отслеживание изменений необходимо включить в таблице. Может использоваться имя таблицы, состоящее из одной, двух, трех или четырех частей. Имя таблицы может быть синонимом таблицы.  
  
 *last_sync_version*  
 При получении изменений вызывающее приложение должно указать точку, с которой необходимы эти изменения. Значение last_sync_version указывает эту точку. Функция возвращает данные обо всех строках, изменившихся начиная с этой версии. Приложение запрашивает изменения с версией, большей, чем значение last_sync_version.  
  
 Как правило, прежде чем он получит изменения, приложение будет вызывать **CHANGE_TRACKING_CURRENT_VERSION()** получить версию, которая будет использоваться далее времени изменения являются обязательными. Поэтому в приложении нет необходимости интерпретировать или разбирать фактическое значение.  
  
 Поскольку значение last_sync_version получается в вызывающем приложении, именно приложение должно хранить указанное значение. Если это значение в приложении будет утеряно, потребуется повторная инициализация данных.  
  
 *значение last_sync_version* — **bigint**. Это значение должно быть скалярным. Использование выражения приведет к возникновению синтаксической ошибки.  
  
 При значении NULL возвращаются все отслеживаемые изменения.  
  
 *значение last_sync_version* следует проверить, чтобы убедиться, что это не слишком старый, так как некоторые или все данные изменений могут быть очищены истечении срока хранения, настроенной для базы данных. Дополнительные сведения см. в разделе [CHANGE_TRACKING_MIN_VALID_VERSION &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md) и [ALTER параметры SET базы данных &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
 ВЕРСИЯ *таблицы*, {< primary_key_values >}  
 Возвращает информацию о последнем изменении указанной строки. Значения первичного ключа должны идентифицировать строку. <primary_key_values> определяет столбцы первичного ключа и указывает значения. Имена первичных ключевых столбцов могут быть указаны в любом порядке.  
  
 *Таблица*  
 Пользовательская таблица для получения информации отслеживания изменений. Отслеживание изменений необходимо включить в таблице. Может использоваться имя таблицы, состоящее из одной, двух, трех или четырех частей. Имя таблицы может быть синонимом таблицы.  
  
 *column_name*  
 Указывает одно или несколько имен первичных ключевых столбцов. Несколько имен столбцов могут быть указаны в любом порядке.  
  
 *Value*  
 Значение первичного ключа. Если существует несколько первичных ключевых столбцов, значения должен быть указан в том же порядке следования столбцов в *column_name* списка.  
  
 [КАК] *table_alias* [(*псевдоним_столбца* [,...*n* ] ) ]  
 Задает имена для результатов, возвращаемых функцией CHANGETABLE.  
  
 *table_alias*  
 Псевдоним таблицы, возвращаемый функцией CHANGETABLE. *table_alias* является обязательным и должен быть допустимым [идентификатор](../../relational-databases/databases/database-identifiers.md).  
  
 *column_alias*  
 Необязательный псевдоним столбца или список псевдонимов столбцов, возвращаемых функцией CHANGETABLE. Обеспечивает возможность настройки имен столбцов в случае, если в результатах присутствуют повторяющиеся имена.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **table**  
  
## <a name="return-values"></a>Возвращаемые значения  
  
### <a name="changetable-changes"></a>CHANGETABLE CHANGES  
 При указании ключевого слова CHANGES возвращается ноль или несколько строк, содержащих следующие столбцы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|SYS_CHANGE_VERSION|**bigint**|Значение версии, связанное с последним изменением в строке|  
|SYS_CHANGE_CREATION_VERSION|**bigint**|Значения версии, связанные с последней операцией вставки.|  
|SYS_CHANGE_OPERATION|**nchar(1)**|Задает тип изменения:<br /><br /> **U** = блокировка обновления<br /><br /> **I** = Insert<br /><br /> **D** = удаление|  
|SYS_CHANGE_COLUMNS|**varbinary(4100)**|Содержит список столбцов, измененных после last_sync_version (базовой версии). Обратите внимание, что вычисляемые столбцы никогда не указаны как измененный.<br /><br /> Принимает значение NULL, если выполняется любое из следующих условий.<br /><br /> Отслеживание изменений столбцов не включено.<br /><br /> Операция представляет собой операцию вставки или удаления.<br /><br /> Все ключевые столбцы, не являющиеся первичными, были обновлены одной операцией. Это двоичное значение не следует интерпретировать непосредственно. Используйте для его интерпретации [CHANGE_TRACKING_IS_COLUMN_IN_MASK()](../../relational-databases/system-functions/change-tracking-is-column-in-mask-transact-sql.md).|  
|SYS_CHANGE_CONTEXT|**varbinary(128)**|Измените контекст, при необходимости можно указать с помощью [WITH](../../relational-databases/system-functions/with-change-tracking-context-transact-sql.md) предложения как часть инструкции INSERT, UPDATE или DELETE.|  
|\<значение первичного ключевого столбца >|Такие же, как столбцы таблицы пользователя|Значения первичного ключа для отслеживаемой таблицы. Эти значения уникально идентифицируют каждую строку в таблице пользователя.|  
  
### <a name="changetable-version"></a>CHANGETABLE VERSION  
 При указании значения VERSION возвращается одна строка, содержащая следующие столбцы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|SYS_CHANGE_VERSION|**bigint**|Текущее значение версии изменений, связанное со строкой.<br /><br /> Принимает значение NULL, если изменение не производилось в течение периода времени, превышающего срок хранения данных отслеживания изменений, либо если строка не изменялась с момента включения отслеживания изменений.|  
|SYS_CHANGE_CONTEXT|**varbinary(128)**|Измените контекст, который указывается дополнительно с использованием предложения WITH как часть инструкции INSERT, UPDATE или DELETE.|  
|\<значение первичного ключевого столбца >|Такие же, как столбцы таблицы пользователя|Значения первичного ключа для отслеживаемой таблицы. Эти значения уникально идентифицируют каждую строку в таблице пользователя.|  
  
## <a name="remarks"></a>Remarks  
 Функция CHANGETABLE обычно используется в предложении FROM запроса, как если бы она была таблицей.  
  
## <a name="changetablechanges"></a>CHANGETABLE(CHANGES...)  
 Чтобы получить данные для новых или измененных строк, соедините результирующий набор с пользовательской таблицей с помощью первичных ключевых столбцов. Для каждой строки в пользовательской таблице, которые были изменены, возвращается только одна строка, даже при наличии нескольких изменений в одну строку с момента *last_sync_version* значение.  
  
 Изменения первичного ключевого столбца никогда не помечаются как обновления. Если значение первичного ключа изменяется, это изменение рассматривается как удаление прежнего значения и вставка нового.  
  
 Если удалить, а затем вставить строку, содержащую тот же первичный ключ, такое изменение рассматривается как обновление для всех столбцов в строке.  
  
 Значения, возвращаемые для столбцов SYS_CHANGE_OPERATION и SYS_CHANGE_COLUMNS, являются относительно базовой (версии last_sync_version), указанный. Например если операция вставки была выполнена в версии 10, операция обновления в версии 15, а базовым *last_sync_version* 12, обновления будут отображаться. Если *last_sync_version* значение 8, будут отображаться инструкции insert. Изменения в вычисляемых столбцах никогда не регистрируются в столбце SYS_CHANGE_COLUMNS как обновления.  
  
 В целом в пользовательских таблицах отслеживаются все операции вставки, обновления и удаления данных, включая инструкцию MERGE.  
  
 Не отслеживаются следующие операции, затрагивающие данные в пользовательских таблицах.  
  
-   Выполнение инструкции UPDATETEXT  
  
     Эта инструкция устарела и в следующей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет удалена. Однако изменения, произведенные с помощью предложения .WRITE инструкции UPDATE, отслеживаются.  
  
-   Удаление строк с помощью инструкции TRUNCATE TABLE  
  
     При усечении таблицы данные отслеживания изменений, связанные с таблицей, будут сброшены, как будто отслеживание изменений для таблицы только что включено. Клиентское приложение должно обязательно произвести синхронизацию версий. Проверка окончится неуспешно, если таблица была усечена.  
  
## <a name="changetableversion"></a>CHANGETABLE(VERSION...)  
 Если указан несуществующий первичный ключ, возвращается пустой результирующий набор.  
  
 SYS_CHANGE_VERSION может иметь значение NULL, если никаких изменений не было внесено в течение периода, превышающего срок хранения (например, при очистке была удалена информация об изменениях), или если строка ни разу не изменялась с момента включения отслеживания изменений для таблицы.  
  
## <a name="permissions"></a>Разрешения  
 Необходимы следующие разрешения для таблицы, который задается параметром *таблицы* значение для получения информации отслеживания изменений:  
  
-   Разрешение SELECT на первичные ключевые столбцы.  
  
-   VIEW CHANGE TRACKING  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-rows-for-an-initial-synchronization-of-data"></a>A. Возврат строк для начальной синхронизации данных  
 В следующем примере показано, как получить данные для исходной синхронизации данных таблицы. Запрос возвращает все данные строк и их связанные версии. Можно затем вставить или добавить эти данные в систему, где будут содержаться синхронизированные данные.  
  
```sql  
-- Get all current rows with associated version  
SELECT e.[Emp ID], e.SSN, e.FirstName, e.LastName,  
    c.SYS_CHANGE_VERSION, c.SYS_CHANGE_CONTEXT  
FROM Employees AS e  
CROSS APPLY CHANGETABLE   
    (VERSION Employees, ([Emp ID], SSN), (e.[Emp ID], e.SSN)) AS c;  
```  
  
### <a name="b-listing-all-changes-that-were-made-since-a-specific-version"></a>Б. Список всех изменений, внесенных после определенной версии  
 В следующем примере показано, как получить список всех изменений, внесенных в таблицу после указанной версии (`@last_sync_version)`. [Emp ID] и SSN являются столбцами составного первичного ключа.  
  
```sql  
DECLARE @last_sync_version bigint;  
SET @last_sync_version = <value obtained from query>;  
SELECT [Emp ID], SSN,  
    SYS_CHANGE_VERSION, SYS_CHANGE_OPERATION,  
    SYS_CHANGE_COLUMNS, SYS_CHANGE_CONTEXT   
FROM CHANGETABLE (CHANGES Employees, @last_sync_version) AS C;  
```  
  
### <a name="c-obtaining-all-changed-data-for-a-synchronization"></a>В. Получение всех измененных данных для синхронизации  
 В следующем примере показано, как можно получить все измененные данные. Этим запросом данные отслеживания изменений объединяются с пользовательской таблицей таким образом, чтобы был выполнен возврат данных пользовательской таблицы. Ключевое слово `LEFT OUTER JOIN` используется для возврата строки для удаленных строк.  
  
```sql  
-- Get all changes (inserts, updates, deletes)  
DECLARE @last_sync_version bigint;  
SET @last_sync_version = <value obtained from query>;  
SELECT e.FirstName, e.LastName, c.[Emp ID], c.SSN,  
    c.SYS_CHANGE_VERSION, c.SYS_CHANGE_OPERATION,  
    c.SYS_CHANGE_COLUMNS, c.SYS_CHANGE_CONTEXT   
FROM CHANGETABLE (CHANGES Employees, @last_sync_version) AS c  
    LEFT OUTER JOIN Employees AS e  
        ON e.[Emp ID] = c.[Emp ID] AND e.SSN = c.SSN;  
```  
  
### <a name="d-detecting-conflicts-by-using-changetableversion"></a>Г. Выявление конфликтов с помощью инструкции CHANGETABLE(VERSION...)  
 В следующем примере показано, как выполнить обновление строки только в случае, если строка не изменялась после последней синхронизации. Номер версии конкретной строки можно получить с помощью функции `CHANGETABLE`. Если строка была обновлена, изменения не вносятся и запрос возвращает данные о самом последнем изменении, внесенном в строку.  
  
```sql  
-- @last_sync_version must be set to a valid value  
UPDATE  
    SalesLT.Product  
SET  
    ListPrice = @new_listprice  
FROM  
    SalesLT.Product AS P  
WHERE  
    ProductID = @product_id AND  
    @last_sync_version >= ISNULL (  
        (SELECT CT.SYS_CHANGE_VERSION FROM   
            CHANGETABLE(VERSION SalesLT.Product,  
            (ProductID), (P.ProductID)) AS CT),  
        0);  
```  
  
## <a name="see-also"></a>См. также  
 [Функции отслеживания изменений (Transact-SQL)](../../relational-databases/system-functions/change-tracking-functions-transact-sql.md)   
 [Отслеживание измененных данных (SQL Server)](../../relational-databases/track-changes/track-data-changes-sql-server.md)   
 [CHANGE_TRACKING_IS_COLUMN_IN_MASK &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-is-column-in-mask-transact-sql.md)   
 [CHANGE_TRACKING_CURRENT_VERSION (Transact-SQL)](../../relational-databases/system-functions/change-tracking-current-version-transact-sql.md)   
 [CHANGE_TRACKING_MIN_VALID_VERSION &#40; Transact-SQL &#41;](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)  
  
  
