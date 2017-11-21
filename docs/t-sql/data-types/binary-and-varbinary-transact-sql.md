---
title: "Binary и varbinary (Transact-SQL) | Документы Microsoft"
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
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e6aaf00b8e846316c92897360932703a013150e8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="binary-and-varbinary-transact-sql"></a>binary и varbinary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Типы двоичных данных фиксированной или переменной длины.
  
## <a name="arguments"></a>Аргументы  
**двоичный** [(  *n*  )] двоичные данные фиксированной длины с длиной  *n*  байт, где  *n*  представляет собой значение от 1 до 8000. Размер хранилища  *n*  байт.
  
**varbinary** [(  *n*   |  **max**)] двоичные данные переменной длины. *n*может иметь значение от 1 до 8000. **Max** указывает, что максимальный размер хранилища равен 2 ^ 31-1 байт. Размер хранения — это фактическая длина введенных данных плюс 2 байта. Введенные данные могут иметь размер 0 символов. ANSI SQL синонимом **varbinary** — **двоичных переменной**.
  
## <a name="remarks"></a>Замечания  
Когда  *n*  не указан в определении данных или в инструкции объявления переменной, длина по умолчанию равна 1. Когда  *n*  не указан в функции CAST, длина по умолчанию равна 30.

| Тип данных | Используется, если... |
| --- | --- |
| **binary** | размеры записей данных столбцов, согласованы.|
| **varbinary** | размеры записей данных столбцов значительно изменяются.|
| **varbinary(max)** | записей данных столбцов превышает 8 000 байт.|


## <a name="converting-binary-and-varbinary-data"></a>Преобразование данных binary и varbinary
Если данные преобразуются из типа данных string (**char**, **varchar**, **nchar**, **nvarchar**, **двоичный файл**, **varbinary**, **текст**, **ntext**, или **изображения**) для **двоичных** или **varbinary** разной длины типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] дополняет или усекает данные справа. Если другие типы данных преобразуются в **двоичных** или **varbinary**, данные дополняются или усекаются слева. Дополнение осуществляется шестнадцатеричными нулями.
  
Преобразование данных для **двоичных** и **varbinary** типы данных полезно, если **двоичных** данных — самый простой способ перемещения данных. Преобразование любого какой-либо введите в двоичное значение большого достаточно размер и затем обратно в тип, всегда приводит к то же значение, если оба преобразования выполняются в той же версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Двоичное представление значения может меняться в зависимости от версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
Вы можете преобразовать **int**, **smallint**, и **tinyint** для **двоичных** или **varbinary**, но если вы преобразовать **двоичных** обратно в целочисленное значение, это значение будет отличаться от исходного целочисленное значение, если произошло усечение. Например, в следующей инструкции SELECT показано, что целочисленное значение `123456` обычно хранится как двоичное `0x0001e240`:
  
```sql
SELECT CAST( 123456 AS BINARY(4) );  
```  
  
Тем не менее следующие `SELECT` инструкции показано, что если **двоичных** целевой слишком мал для хранения всего значения, начальные цифры неявно усекаются, чтобы тот же номер хранится в виде `0xe240`:
  
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
>  Преобразования между данными любого типа и **двоичных** типы данных не обязательно будет одинаковым в разных версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Преобразование типов данных &#40; компонент Database Engine &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)
  
  

