---
title: Типы char и varchar (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- varchar
- varchar_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fixed-length data types [SQL Server]
- character data type
- char data type
- varchar(max) data type
- variable-length data types [SQL Server]
- varchar data type
- utf8
ms.assetid: 282cd982-f4fb-4b22-b2df-9e8478f13f6a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e8b54eff8007a5edd33ed36f40514a2e53b579f5
ms.sourcegitcommit: eddf8cede905d2adb3468d00220a347acd31ae8d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/24/2018
ms.locfileid: "49960798"
---
# <a name="char-and-varchar-transact-sql"></a>Типы char и varchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Типы данных char имеют фиксированную (**char**) или переменную (**varchar**) длину. Начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] при использовании параметров сортировки с поддержкой UTF-8 эти типы данных хранят весь диапазон символьных данных [Юникод](../../relational-databases/collations/collation-and-unicode-support.md#Unicode_Defn) и используют кодировку [UTF-8](http://www.wikipedia.org/wiki/UTF-8). Если указаны параметры сортировки без поддержки UTF-8, эти типы данных хранят только подмножество символьных данных, поддерживаемых соответствующей кодовой страницей указанных параметров сортировки.
  
## <a name="arguments"></a>Аргументы  
**char** [ ( *n* ) ] — строковые данные фиксированной длины. *n* определяет длину строки в байтах и должно иметь значение от 1 до 8000. Для однобайтовых кодировок, таких как *Latin*, размер при хранении равен *n* байт, а количество хранимых символов — тоже *n*. Для многобайтовых кодировок размер при хранения тоже равен *n* байт, но количество хранимых символов может быть меньше *n*. Синонимом по стандарту ISO для типа **char** является **character**. Дополнительные сведения о кодировках см. в статье [Однобайтовые и многобайтовые кодировки](/cpp/c-runtime-library/single-byte-and-multibyte-character-sets).

**varchar** [ ( *n* | **max** ) ] — строковые данные переменной длины. *n* определяет длину строки в байтах и может иметь значение от 1 до 8000. Значение **max** указывает, что максимальный размер при хранении составляет 2^31-1 байт (2 ГБ). Для однобайтовых кодировок, таких как *Latin*, размер при хранении равен *n* байт + 2 байта, а количество хранимых символов — *n*. Для многобайтовых кодировок размер при хранения тоже равен *n* байт + 2 байта, но количество хранимых символов может быть меньше *n*. Синонимами по стандарту ISO для типа **varchar** являются типы **charvarying** или **charactervarying**. Дополнительные сведения о кодировках см. в статье [Однобайтовые и многобайтовые кодировки](/cpp/c-runtime-library/single-byte-and-multibyte-character-sets).

## <a name="remarks"></a>Remarks  
Если значение *n* в определении данных или в инструкции объявления переменной не указано, то длина по умолчанию равна 1. Если значение *n* не указано при использовании функций CAST и CONVERT, длина по умолчанию равна 30.
  
Объектам, в которых используются типы данных **char** и **varchar**, назначаются параметры сортировки базы данных по умолчанию, если только иные параметры сортировки не назначены с использованием предложения COLLATE. Параметры сортировки контролируют кодовую страницу, используемую для хранения символьных данных.

В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] многобайтовые кодировки включают:
-   двухбайтовые кодировки (DBCS) для некоторых языков Восточной Азии, использующих кодовые страницы 936 и 950 (китайский), 932 (японский) или 949 (корейский).
-   UTF-8 с кодовой страницей 65001. **Относится к** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]).

Если у вас есть сайты, поддерживающие несколько языков, примите к сведению следующие рекомендации:
- Для поддержки Юникода и минимизации проблем с преобразованием символов рекомендуем использовать параметры сортировки с поддержкой UTF-8 (начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]). 
- Если используется более ранняя версия [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], то чтобы избежать проблем с преобразованием символов, рекомендуем использовать типы данных Юникода **nchar** или **nvarchar**.   

Если вы используете **char** или **varchar**, мы рекомендуем:
- Если размеры записей данных столбцов постоянны, используйте **char**.  
- Если размеры записей данных столбцов значительно изменяются, используйте **varchar**.  
- использовать **varchar(max)**, если размеры записей данных в столбцах существенно отличаются и длина строки может превышать 8000 байт.  
  
Если SET ANSI_PADDING равно OFF при выполнении CREATE TABLE или ALTER TABLE, столбец **char**, определенный как NULL, обрабатывается как **varchar**.
  
> [!WARNING]
> Для каждого ненулевого столбца varchar(max) или nvarchar(max) требуется 24 байта дополнительного фиксированного выделения, которые учитываются в максимальном размере строки в 8060 байт во время операции сортировки. Это может создать неявное ограничение в ряде ненулевых столбцов varchar(max) или nvarchar(max), которые могут быть созданы в таблице.  
При создании таблицы или во время вставки данных не возникает особых ошибок (кроме обычного предупреждения о том, что максимальный размер строки превышает максимально допустимое значение в 8060 байт). Этот крупный размер строки может вызывать ошибки (например, ошибку 512) во время некоторых обычных операций, таких как обновление ключа кластеризованного индекса, или сортировать полный набор столбцов, который пользователи не могут использовать до выполнения операции.
  
##  <a name="_character"></a> Преобразование символьных данных  
При преобразовании символьного выражения в символьный тип данных другой длины значения, слишком длинные для нового типа данных, усекаются. Тип **uniqueidentifier** считается символьным типом при преобразовании из символьного выражения, поэтому на него распространяются правила усечения при преобразовании в символьный тип. См подраздел «Примеры» ниже.
  
Если символьное выражение преобразуется в символьное выражение другого типа данных или размера, например из **char(5)** в **varchar(5)** или из **char(20)** в **char(15)**, то преобразованному значению присваиваются параметры сортировки входного значения. Если несимвольное выражение преобразуется в символьный тип данных, то преобразованному значению присваиваются параметры сортировки, заданные по умолчанию в текущей базе данных. В любом случае необходимые параметры сортировки можно присвоить с помощью предложения [COLLATE](../../t-sql/statements/collations.md).
  
> [!NOTE]  
> Преобразование кодовых страниц поддерживается для типов данных **char** и **varchar**, однако поддержка типа данных **text** не предусмотрена. Как и в ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], о потере данных во время преобразования кодовых страниц не сообщается.  
  
Символьные выражения, которые преобразуются в приближенный тип данных **numeric**, могут содержать необязательную экспоненциальную нотацию (символ e нижнего регистра или E верхнего регистра, за которым следуют необязательный знак плюс (+) или минус (–) и число).
  
Символьные выражения, преобразуемые в точный тип данных **numeric**, должны состоять из цифр, десятичного разделителя и необязательного знака плюс (+) или минус (–). Начальные пробелы не учитываются. Разделители в виде запятой запрещены (например, десятичный разделитель в числе 123 456,00).
  
Кроме того, символьные выражения, преобразуемые в типы данных **money** или **smallmoney**, могут содержать необязательный десятичный разделитель и обозначение валюты. Разрешаются разделители в виде запятой, например 123 456,00 руб.
  
## <a name="examples"></a>Примеры  
  
### <a name="a-showing-the-default-value-of-n-when-used-in-variable-declaration"></a>A. Отображение значения по умолчанию n при использовании в объявлении переменной.  
В приведенном ниже примере показано, что значение по умолчанию *n* равно 1 для типов данных `char` и `varchar`, если они используются в объявлении переменной.
  
```sql
DECLARE @myVariable AS varchar = 'abc';  
DECLARE @myNextVariable AS char = 'abc';  
--The following returns 1  
SELECT DATALENGTH(@myVariable), DATALENGTH(@myNextVariable);  
GO  
```  
  
### <a name="b-showing-the-default-value-of-n-when-varchar-is-used-with-cast-and-convert"></a>Б. Отображение значения по умолчанию n при использовании функций CAST и CONVERT с типом данных varchar.  
В приведенном ниже примере показано, что значение по умолчанию *n* равно 30, если типы данных `char` или `varchar` используются с функциями `CAST` и `CONVERT`.
  
```sql
DECLARE @myVariable AS varchar(40);  
SET @myVariable = 'This string is longer than thirty characters';  
SELECT CAST(@myVariable AS varchar);  
SELECT DATALENGTH(CAST(@myVariable AS varchar)) AS 'VarcharDefaultLength';  
SELECT CONVERT(char, @myVariable);  
SELECT DATALENGTH(CONVERT(char, @myVariable)) AS 'VarcharDefaultLength';  
```  
  
### <a name="c-converting-data-for-display-purposes"></a>В. Преобразование данных для отображения  
В следующем примере два столбца преобразуются в символьные типы, после чего к ним применяется стиль, применяющий к отображаемым данным конкретный формат. Тип **money** преобразуется в символьные данные. К нему применяется стиль 1, отображающий значения с запятыми между каждой группой из трех цифр, отсчитывая влево от десятичной точи, и каждой группой из двух цифр, отсчитывая вправо от десятичной точки. Тип **datetime** преобразуется в символьные данные. К нему применяется стиль 3, отображающий данные в формате дд/мм/гг. В предложении WHERE тип **money** приводится к символьному типу для выполнения операции сравнения строк.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT  BusinessEntityID,   
   SalesYTD,   
   CONVERT (varchar(12),SalesYTD,1) AS MoneyDisplayStyle1,   
   GETDATE() AS CurrentDate,   
   CONVERT(varchar(12), GETDATE(), 3) AS DateDisplayStyle3  
FROM Sales.SalesPerson  
WHERE CAST(SalesYTD AS varchar(20) ) LIKE '1%';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
BusinessEntityID SalesYTD              DisplayFormat CurrentDate             DisplayDateFormat  
---------------- --------------------- ------------- ----------------------- -----------------  
278              1453719.4653          1,453,719.47  2011-05-07 14:29:01.193 07/05/11  
280              1352577.1325          1,352,577.13  2011-05-07 14:29:01.193 07/05/11  
283              1573012.9383          1,573,012.94  2011-05-07 14:29:01.193 07/05/11  
284              1576562.1966          1,576,562.20  2011-05-07 14:29:01.193 07/05/11  
285              172524.4512           172,524.45    2011-05-07 14:29:01.193 07/05/11  
286              1421810.9242          1,421,810.92  2011-05-07 14:29:01.193 07/05/11  
288              1827066.7118          1,827,066.71  2011-05-07 14:29:01.193 07/05/11  
```  
  
### <a name="d-converting-uniqueidentifer-data"></a>Г. Преобразование данных uniqueidentifier  
В следующем примере значение `uniqueidentifier` преобразуется в тип данных `char`.
  
```sql
DECLARE @myid uniqueidentifier = NEWID();  
SELECT CONVERT(char(255), @myid) AS 'char';  
```  
  
Следующий пример показывает усечение данных, когда значение является слишком длинным для преобразования в заданный тип данных. Так как тип данных **uniqueidentifier** ограничен 36 символами, все символы, выходящие за пределы этой длины, будут усечены.
  
```sql
DECLARE @ID nvarchar(max) = N'0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong';  
SELECT @ID, CONVERT(uniqueidentifier, @ID) AS TruncatedValue;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
String                                       TruncatedValue  
-------------------------------------------- ------------------------------------  
0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong    0E984725-C51C-4BF4-9960-E1C80E27ABA0  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также раздел
[nchar и nvarchar (Transact-SQL)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[COLLATE (Transact-SQL)](../../t-sql/statements/collations.md)  
[Преобразование типов данных (ядро СУБД)](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[Оценка размера базы данных](../../relational-databases/databases/estimate-the-size-of-a-database.md)     
[Поддержка параметров сортировки и Юникода](../../relational-databases/collations/collation-and-unicode-support.md)    
[Однобайтовые и многобайтовые кодировки](/cpp/c-runtime-library/single-byte-and-multibyte-character-sets)
  
