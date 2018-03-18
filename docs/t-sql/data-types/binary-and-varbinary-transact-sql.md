---
title: "binary и varbinary (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 8/16/2017
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4ad5bce3cacc0f892f7087df785da8cedcb4e932
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="binary-and-varbinary-transact-sql"></a>binary и varbinary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Типы двоичных данных фиксированной или переменной длины.
  
## <a name="arguments"></a>Аргументы  
**binary** [ ( *n* ) ] Двоичные данные фиксированной длины размером в *n* байт, где *n* — значение от 1 до 8000. Размер при хранении составляет *n* байт.
  
**varbinary** [ ( *n* | **max**) ] Двоичные данные с переменной длиной. *n* может иметь значение от 1 до 8000. Значение **max** указывает, что максимальный размер при хранении составляет 2^31-1 байт. Размер хранения — это фактическая длина введенных данных плюс 2 байта. Введенные данные могут иметь размер 0 символов. В ANSI SQL синонимом для **varbinary** является **binary varying**.
  
## <a name="remarks"></a>Remarks  
Если значение *n* при определении данных или в инструкции объявления переменной не указано, то длина по умолчанию равна 1. Если значение *n* не указано в функции CAST, длина по умолчанию равна 30.

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
  
  
