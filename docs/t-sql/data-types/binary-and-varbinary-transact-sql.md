---
title: binary и varbinary (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 8/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- binary_TSQL
- varbinary_TSQL
- binary
- varbinary
dev_langs:
- TSQL
helpviewer_keywords:
- varbinary data type
- binary [SQL Server], about binary data type
ms.assetid: bcce65f9-10db-4b3e-bfaf-dfc06c6f820f
caps.latest.revision: 27
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6398547d9e8c8daafacc62feeebe378cc069c179
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43068026"
---
# <a name="binary-and-varbinary-transact-sql"></a>binary и varbinary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Типы двоичных данных фиксированной или переменной длины.
  
## <a name="arguments"></a>Аргументы  
**binary** [ ( *n* ) ] Двоичные данные фиксированной длины размером в *n*байт, где *n* — значение от 1 до 8000. Размер при хранении составляет *n* байт.
  
**varbinary** [ ( *n* | **max**) ] Двоичные данные с переменной длиной. *n* может иметь значение от 1 до 8000. Значение **max** указывает, что максимальный размер при хранении составляет 2^31-1 байт. Размер хранения — это фактическая длина введенных данных плюс 2 байта. Введенные данные могут иметь размер 0 символов. В ANSI SQL синонимом для **varbinary** является **binary varying**.
  
## <a name="remarks"></a>Remarks  
Если значение *n* в определении данных или в инструкции объявления переменной не указано, то длина по умолчанию равна 1. Когда *n* не задано функцией CAST, длина по умолчанию равняется 30.

| Тип данных | Применение |
| --- | --- |
| **binary** | Размер данных в столбце одинаков.|
| **varbinary** | Данные в столбце значительно различаются по размеру.|
| **varbinary(max)** | Длина элементов данных в столбце превышает 8000 байт.|


## <a name="converting-binary-and-varbinary-data"></a>Преобразование типов данных binary и varbinary
При преобразовании данных строкового типа (**char**, **varchar**, **nchar**, **nvarchar**, **binary**, **varbinary**, **text**, **ntext** или **image**) в тип данных **binary** или **varbinary** неравной длины [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] дополняет или усекает данные справа. При преобразовании других типов данных в тип **binary** или **varbinary** данные дополняются или усекаются слева. Дополнение осуществляется шестнадцатеричными нулями.
  
Если для обмена данными лучше всего подходит тип **binary**, то другие типы данных удобнее всего будет преобразовать в **binary** и **varbinary**. Преобразование любого достаточно большого значения в двоичное и обратно всегда дает первоначальное значение, если оба преобразования выполняются в одной и той же версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Двоичное представление значения может меняться в зависимости от версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
Типы данных **int**, **smallint** и **tinyint** можно преобразовать в тип **binary** или **varbinary**, но если преобразовать значение **binary** обратно в целочисленное, то оно будет отличаться от исходного в случае усечения. Например, в следующей инструкции SELECT показано, что целочисленное значение `123456` обычно хранится как двоичное `0x0001e240`:
  
```sql
SELECT CAST( 123456 AS BINARY(4) );  
```  
  
Однако в следующей инструкции `SELECT` показано, что если целевой тип **binary** слишком мал для хранения всего значения, то начальные цифры неявно усекаются и то же самое число хранится как `0xe240`:
  
```sql
SELECT CAST( 123456 AS BINARY(2) );  
```  
  
В следующем пакете показано, что это необъявленное усечение может повлиять на арифметические операции без возникновения ошибки.
  
```sql
DECLARE @BinaryVariable2 BINARY(2);  
  
SET @BinaryVariable2 = 123456;  
SET @BinaryVariable2 = @BinaryVariable2 + 1;  
  
SELECT CAST( @BinaryVariable2 AS INT);  
GO  
```  
  
Окончательный результат — `57921`, но не `123457`.
  
> [!NOTE]  
>  Преобразование любого типа данных в **binary** может различаться в зависимости от версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также раздел
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Преобразование типов данных (ядро СУБД)](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)
  
  
