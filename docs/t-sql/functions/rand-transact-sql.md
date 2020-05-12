---
title: RAND (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- RAND
- RAND_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RAND function
- values [SQL Server], random float
- random float value
ms.assetid: 363c84d6-b9fa-49ba-9a75-e44f27535ff6
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0c6df52fdaa5108c6cab057573f34d0f545f94c4
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82823779"
---
# <a name="rand-transact-sql"></a>RAND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Возвращает псевдослучайное значение типа **float** от 0 до 1.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RAND ( [ seed ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *seed*  
 Целочисленное [выражение](../../t-sql/language-elements/expressions-transact-sql.md) (**tinyint**, **smallint** или **int**), задающее начальное значение. Если аргумент *seed* не указан, компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] использует случайное начальное значение. Для указанного начального значения возвращаемый результат всегда будет один и тот же.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **float**  
  
## <a name="remarks"></a>Remarks  
 Повторные вызовы RAND() с одинаковым начальным значением возвращают одинаковые результаты.  
  
 Для одного соединения, если RAND() вызван с конкретным начальным значением, все последующие вызовы RAND() выдадут результат, основанный на начальном вызове RAND(). Например, следующий запрос всегда будет возвращать ту же последовательность чисел.  
  
```sql  
SELECT RAND(100), RAND(), RAND()   
```  
  
## <a name="examples"></a>Примеры  
 Следующий пример выдает четыре различных случайных числа, сформированных функцией RAND.  
  
```sql  
DECLARE @counter smallint;  
SET @counter = 1;  
WHILE @counter < 5  
   BEGIN  
      SELECT RAND() Random_Number  
      SET @counter = @counter + 1  
   END;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Математические функции (Transact-SQL)](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  
