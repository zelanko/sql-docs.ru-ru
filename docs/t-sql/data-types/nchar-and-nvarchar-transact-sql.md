---
title: "Типы nchar и nvarchar (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- nvarchar data type
- nchar data type
ms.assetid: 81ee5637-ee31-4c4d-96d0-56c26a742354
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4c3f2e9ad1d63992be8f4e4a4c65d821fae73389
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="nchar-and-nvarchar-transact-sql"></a>nchar и nvarchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Символьные типы данных, имеющие постоянную длину, **nchar** или переменную длину, **nvarchar**, содержащие данные в Юникоде и использующие кодировку UCS-2.
  
## <a name="arguments"></a>Аргументы  
**nchar** [ ( n ) ]  
Строковые данные постоянной длины в Юникоде. *n* определяет длину строки и должно иметь значение от 1 до 4000. Размер при хранении составляет удвоенное значение *n* в байтах. Если кодовая страница параметров сортировки использует двухбайтовые символы, размер хранения остается равным *n* байт. В зависимости от символьной строки для хранения *n* символов может понадобиться менее *n* байт. Синонимами типа **nchar** по стандарту ISO являются типы **national char** и **national character**.
  
**nvarchar** [ ( n | **max** ) ]  
Строковые данные переменной длины в Юникоде. *n* определяет длину строки и может иметь значение от 1 до 4000. Значение **max** указывает, что максимальный размер при хранении составляет 2^31-1 символов (2 ГБ). Размер хранилища в байтах вдвое больше числа введенных символов + 2 байта. Синонимами типа **nvarchar** по стандарту ISO являются типы **national char varying** и **national character varying**.
  
## <a name="remarks"></a>Remarks  
Если значение *n* при определении данных или в инструкции объявления переменной не указано, то длина по умолчанию равна 1. Если значение *n* не указано в функции CAST, длина по умолчанию равна 30.
  
Рекомендуется использовать **nchar**, если размеры элементов данных в столбцах предполагаются сходные.
  
Рекомендуется использовать **nvarchar**, если размеры элементов данных в столбцах предполагаются различные.
  
Тип **sysname** — это предоставляемый системой определяемый пользователем тип данных, который функционально эквивалентен типу **nvarchar(128)** за исключением того, что он не допускает значения NULL. Тип **sysname** используется для ссылки на имена объектов баз данных.
  
Объектам, в которых используются типы данных **nchar** и **nvarchar**, назначаются параметры сортировки базы данных по умолчанию, если только иные параметры сортировки не назначены с помощью предложения COLLATE.
  
Для типов данных **nchar** и **nvarchar** параметр SET ANSI_PADDING всегда принимает значение ON. Параметр SET ANSI_PADDING OFF не применяется к типам данных **nchar** или **nvarchar**.
  
Установите префикс символьных строковых констант в кодировке Юникод в виде буквы N. Без префикса N строка преобразуется в кодовую страницу базы данных по умолчанию. Кодовая страница по умолчанию может не распознавать определенные символы.
 
> [!NOTE]  
>  Когда строковая константа имеет префикс в виде буквы N, результатом неявного преобразования является строка Юникода, если длина преобразуемой константы не превышает максимальное значение строкового типа данных Юникода (4000). В противном случае результатом неявного преобразования является большое значение в кодировке Юникод (max).
  
> [!WARNING]  
>  Для каждого ненулевого столбца **varchar(max)** или **nvarchar(max)** требуется 24 байта дополнительного фиксированного выделения, которые учитываются в максимальном размере строки в 8060 байт во время операции сортировки. Это может неявно ограничивать число ненулевых столбцов **varchar(max)** или **nvarchar(max)**, которые могут быть созданы в таблице. При создании таблицы или во время вставки данных не возникает особых ошибок (кроме обычного предупреждения о том, что максимальный размер строки превышает максимально допустимое значение в 8060 байт). Этот крупный размер строки может вызывать ошибки (например, ошибку 512) во время некоторых обычных операций, таких как обновление ключа кластеризованного индекса, или сортировать полный набор столбцов, который пользователи не могут использовать до выполнения операции.  
  
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
  
  
