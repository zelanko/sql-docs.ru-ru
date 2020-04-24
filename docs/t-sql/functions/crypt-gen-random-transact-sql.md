---
title: CRYPT_GEN_RANDOM (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CRYPT_GEN_RANDOM_TSQL
- CRYPT_GEN_RANDOM
dev_langs:
- TSQL
helpviewer_keywords:
- CRYPT_GEN_RANDOM function
ms.assetid: b74bd9d4-758e-4b94-89a0-76dcda6d8c42
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 45f83c409196882e578608b9974d74f4f0f42308
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81626429"
---
# <a name="crypt_gen_random-transact-sql"></a>CRYPT_GEN_RANDOM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Эта функция возвращает криптографическое случайное число, сгенерированное криптографическим API-интерфейсом (CAPI). `CRYPT_GEN_RANDOM` возвращает шестнадцатеричное число, состоящее из указанного числа байтов.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
CRYPT_GEN_RANDOM ( length [ , seed ] )   
```  
  
## <a name="arguments"></a>Аргументы  
*length*  
Длина в байтах создаваемого `CRYPT_GEN_RANDOM` числа. Аргумент *length* имеет тип данных **int** и диапазон значений от 1 до 8000. `CRYPT_GEN_RANDOM` возвращает значение NULL для значения **int** за пределами этого диапазона. 
  
*seed*  
Необязательное шестнадцатеричное число для использования в качестве случайного значения seed. Длина аргумента *seed* должна совпадать со значением аргумента *length*. Аргумент *seed* имеет тип данных **varbinary(8000)** .
  
## <a name="returned-types"></a>Возвращаемые типы  
**varbinary(8000)**
  
## <a name="permissions"></a>Разрешения  
Эта функция является открытой, поэтому не требует специальных разрешений.
  
## <a name="examples"></a>Примеры  
  
### <a name="a-generating-a-random-number"></a>A. Формирование случайного числа  
В этом примере генерируется случайное число длиной 50 байт.
  
```sql
SELECT CRYPT_GEN_RANDOM(50) ;  
```  
  
В этом примере генерируется случайное число длиной 4 байт с использованием 4-байтного значения seed:
  
```sql
SELECT CRYPT_GEN_RANDOM(4, 0x25F18060) ;  
```  
  
## <a name="see-also"></a>См. также раздел
[RAND (Transact-SQL)](../../t-sql/functions/rand-transact-sql.md)
  
  
