---
title: "nchar и nvarchar (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- nvarchar data type
- nchar data type
ms.assetid: 81ee5637-ee31-4c4d-96d0-56c26a742354
caps.latest.revision: "44"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4c3f2e9ad1d63992be8f4e4a4c65d821fae73389
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="nchar-and-nvarchar-transact-sql"></a>nchar и nvarchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Символьные типы данных, которые являются либо фиксированной длины, **nchar**, или переменную длину, **nvarchar**, набор символов в Юникоде и использование ЮНИКОДА UCS-2.
  
## <a name="arguments"></a>Аргументы  
**nchar** ([n])  
Строковые данные постоянной длины в Юникоде. *n*Определяет длину строки и должен быть значением от 1 до 4000. Размер хранения составляет два раза  *n*  байт. Если кодовая страница параметров сортировки использует двухбайтовые символы, размер хранения остается  *n*  байт. В зависимости от строки, размер хранилища  *n*  байтов может быть меньше, чем значение, указанное для  *n* . Синонимами по стандарту ISO для **nchar** , **national char** и **символов национального алфавита**...
  
**nvarchar** [(n | **max** )]  
Строковые данные переменной длины в Юникоде. *n*Определяет длину строки и может принимать значение от 1 до 4000. **Max** указывает, что максимальный размер хранилища равен 2 ^ 31-1 символов (2 ГБ). Размер хранилища в байтах вдвое больше числа введенных символов + 2 байта. Синонимами по стандарту ISO для **nvarchar** , **national char переменной** и **символов национального алфавита переменной**.
  
## <a name="remarks"></a>Замечания  
Когда  *n*  не указан в определении данных или в инструкции объявления переменной, длина по умолчанию равна 1. Когда  *n*  не указан в функции CAST, длина по умолчанию равна 30.
  
Используйте **nchar** Если размеры элементов данных в столбцах предполагаются схожи.
  
Используйте **nvarchar** Если размеры элементов данных в столбцах предполагаются различные.
  
**sysname** — предоставляемый системой определяемый пользователем тип, который функционально эквивалентен **nvarchar(128)**, за исключением того, что не допускает значения NULL. **sysname** используется для ссылок на имена объектов базы данных.
  
Объекты, использующие **nchar** или **nvarchar** присваиваются параметры сортировки по умолчанию базы данных, назначенный конкретные параметры сортировки предложением COLLATE.
  
SET ANSI_PADDING всегда установлен на ON **nchar** и **nvarchar**. SET ANSI_PADDING OFF не применяется к **nchar** или **nvarchar** типов данных.
  
Префикс строковым константам в Юникоде буква N. Без префикса N строка преобразуется в кодовую страницу по умолчанию базы данных. Кодовая страница по умолчанию может не распознавать определенные символы.
 
> [!NOTE]  
>  После добавления префикса строковой константы с букв N, неявное преобразование приведет строка в Юникоде, если константа для преобразования не превышает ограничение максимальной длины для тип данных строки Юникода (4000). В противном случае приведет к неявного преобразования Юникода большого размера (max).
  
> [!WARNING]  
>  Каждый непустой **varchar(max)** или **nvarchar(max)** столбца требуется 24 байта дополнительного фиксированного выделения, которые учитываются ограничение строки 8060 байт во время операции сортировки. Это может создать неявное ограничение на число непустых **varchar(max)** или **nvarchar(max)** столбцы, которые могут быть созданы в таблице. При создании таблицы или во время вставки данных не возникает особых ошибок (кроме обычного предупреждения о том, что максимальный размер строки превышает максимально допустимое значение в 8060 байт). Этот крупный размер строки может вызывать ошибки (например, ошибку 512) во время некоторых обычных операций, таких как обновление ключа кластеризованного индекса, или сортировать полный набор столбцов, который пользователи не могут использовать до выполнения операции.  
  
## <a name="converting-character-data"></a>Преобразование в символьные данные  
Сведения о преобразовании символьных данных см. в разделе [char и varchar &#40; Transact-SQL &#41; ](../../t-sql/data-types/char-and-varchar-transact-sql.md).
  
## <a name="examples"></a>Примеры  
  
```sql
CREATE TABLE dbo.MyTable  
(  
  MyNCharColumn nchar(15)  
,MyNVarCharColumn nvarchar(20)
  
);  
  
GO  
INSERT INTO dbo.MyTable VALUES (N'Test data', N'More test data');  
GO  
SELECT MyNCharColumn, MyNVarCharColumn  
FROM dbo.MyTable;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
MyNCharColumn   MyNVarCharColumn  
--------------- --------------------  
Test data       More test data  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[COLLATE &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[КАК &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)  
[SET ANSI_PADDING &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Поддержка параметров сортировки и Юникода](../../relational-databases/collations/collation-and-unicode-support.md)
  
  
