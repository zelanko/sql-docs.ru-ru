---
description: CRYPT_GEN_RANDOM (Transact-SQL)
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
ms.openlocfilehash: d0cdca25e14d58270185d4605287d22d1af5e0d2
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96118621"
---
# <a name="crypt_gen_random-transact-sql"></a>CRYPT_GEN_RANDOM (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Эта функция возвращает криптографическое случайное число, сгенерированное криптографическим API-интерфейсом (CAPI). `CRYPT_GEN_RANDOM` возвращает шестнадцатеричное число, состоящее из указанного числа байтов.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
CRYPT_GEN_RANDOM ( length [ , seed ] )   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
*length*  
Длина в байтах создаваемого `CRYPT_GEN_RANDOM` числа. Аргумент *length* имеет тип данных **int** и диапазон значений от 1 до 8000. `CRYPT_GEN_RANDOM` возвращает значение NULL для значения **int** за пределами этого диапазона. 
  
*seed*  
Необязательное шестнадцатеричное число для использования в качестве случайного значения seed. Длина аргумента *seed* должна совпадать со значением аргумента *length*. Аргумент *seed* имеет тип данных **varbinary(8000)**.
  
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
  
  
