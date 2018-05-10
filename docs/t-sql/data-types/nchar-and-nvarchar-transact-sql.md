---
title: Типы nchar и nvarchar (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- nvarchar data type
- nchar data type
ms.assetid: 81ee5637-ee31-4c4d-96d0-56c26a742354
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f8918d985423174f09e1d796a406cc979dfc61f6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="nchar-and-nvarchar-transact-sql"></a>nchar и nvarchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Символьные типы данных, имеющие постоянную длину, **nchar** или переменную длину, **nvarchar**, содержащие данные в Юникоде и использующие кодировку UCS-2.
  
## <a name="arguments"></a>Аргументы  
**nchar** [ ( n ) ]  
Строковые данные постоянной длины в Юникоде. *n* определяет длину строки и должно иметь значение от 1 до 4000. Размер хранилища — дважды *n* байт. Если кодовая страница параметров сортировки использует двухбайтовые символы, размер хранения остается равным *n* байт. В зависимости от строки для хранения *n* символов может понадобиться менее *n* байт. Синонимами типа **nchar** по стандарту ISO являются типы **national char** и **national character**.
  
**nvarchar** [ ( n | **max** ) ]  
Строковые данные переменной длины в Юникоде. *n* определяет длину строки и может иметь значение от 1 до 4000. Значение **max** указывает, что максимальный размер при хранении составляет 2^30-1 символов.  Максимальный размер при хранении в байтах равен 2 ГБ. Фактический размер хранилища в байтах вдвое больше числа введенных символов + 2 байта. Синонимами типа **nvarchar** по стандарту ISO являются типы **national char varying** и **national character varying**.
  
## <a name="remarks"></a>Remarks  
Если значение *n* в определении данных или в инструкции объявления переменной не указано, то длина по умолчанию равна 1. Когда *n* не задано функцией CAST, длина по умолчанию равняется 30.
  
Рекомендуется использовать **nchar**, если размеры элементов данных в столбцах предполагаются сходные.
  
Рекомендуется использовать **nvarchar**, если размеры элементов данных в столбцах предполагаются различные.
  
Тип **sysname** — это предоставляемый системой определяемый пользователем тип данных, который функционально эквивалентен типу **nvarchar(128)** за исключением того, что он не допускает значения NULL. Тип **sysname** используется для ссылки на имена объектов баз данных.
  
Объектам, в которых используются типы данных **nchar** и **nvarchar**, назначаются параметры сортировки базы данных по умолчанию, если только иные параметры сортировки не назначены с помощью предложения COLLATE.
  
Для типов данных **nchar** и **nvarchar** параметр SET ANSI_PADDING всегда принимает значение ON. Параметр SET ANSI_PADDING OFF не применяется к типам данных **nchar** или **nvarchar**.
  
Установите префикс символьных строковых констант в кодировке Юникод в виде буквы N. Без префикса N строка преобразуется в кодовую страницу базы данных по умолчанию. Кодовая страница по умолчанию может не распознавать определенные символы.
 
> [!NOTE]  
>  Когда строковая константа имеет префикс в виде буквы N, результатом неявного преобразования является строка Юникода, если длина преобразуемой константы не превышает максимальное значение строкового типа данных Юникода (4000). В противном случае результатом неявного преобразования является большое значение в кодировке Юникод (max).
  
> [!WARNING]  
>  Для каждого ненулевого столбца **varchar(max)** или **nvarchar(max)** требуется 24 байта дополнительного фиксированного выделения, которые учитываются в максимальном размере строки в 8060 байт во время операции сортировки. Эти дополнительные байты могут неявно ограничивать число ненулевых столбцов **varchar(max)** или **nvarchar(max)** в таблице. При создании таблицы или во время вставки данных не возникает особых ошибок (кроме обычного предупреждения о том, что максимальный размер строки превышает максимально допустимое значение в 8060 байт). Такой большой размер строки может приводить к ошибкам (например, ошибке 512), которые пользователи не ожидают во время обычных операций.  Примерами операций могут служить обновление ключа кластеризованного индекса или сортировка полного набора столбцов.
  
## <a name="converting-character-data"></a>Преобразование в символьные данные  
Сведения о преобразовании символьных данных см. в статье [char и varchar (Transact-SQL)](../../t-sql/data-types/char-and-varchar-transact-sql.md).
  
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
  
## <a name="see-also"></a>См. также раздел
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[LIKE (Transact-SQL)](../../t-sql/language-elements/like-transact-sql.md)  
[SET ANSI_PADDING (Transact-SQL)](../../t-sql/statements/set-ansi-padding-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Поддержка параметров сортировки и Юникода](../../relational-databases/collations/collation-and-unicode-support.md)
  
  
