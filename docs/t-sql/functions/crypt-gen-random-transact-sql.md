---
title: "CRYPT_GEN_RANDOM (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CRYPT_GEN_RANDOM_TSQL
- CRYPT_GEN_RANDOM
dev_langs:
- TSQL
helpviewer_keywords:
- CRYPT_GEN_RANDOM function
ms.assetid: b74bd9d4-758e-4b94-89a0-76dcda6d8c42
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 695af04a3ee411392cf00be6b6483c9338a4c989
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="cryptgenrandom-transact-sql"></a>CRYPT_GEN_RANDOM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает криптографическое случайное число, сформированное криптографическим API-интерфейсом (CAPI). Выход является шестнадцатеричным числом, состоящим из указанного числа байтов.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CRYPT_GEN_RANDOM ( length [ , seed ] )   
```  
  
## <a name="arguments"></a>Аргументы  
*length*  
Длина создаваемого числа. Максимально — 8000. *Длина* — тип **int**.
  
*Начальное значение*  
Необязательные данные для начального значения.  Должен существовать по крайней мере *длина* байт данных. *Начальное значение* — **varbinary(8000)**.
  
## <a name="returned-types"></a>Возвращаемые типы  
**varbinary(8000)**
  
## <a name="permissions"></a>Permissions  
Эта функция является открытой, поэтому не требует специальных разрешений.
  
## <a name="examples"></a>Примеры  
  
### <a name="a-generating-a-random-number"></a>A. Формирование случайного числа  
В следующем примере формируется случайное число длиной 50 байт.
  
```sql
SELECT CRYPT_GEN_RANDOM(50) ;  
```  
  
В следующем примере формируется случайное число длиной 4 байта с помощью 4-байтного начального значения.
  
```sql
SELECT CRYPT_GEN_RANDOM(4, 0x25F18060) ;  
```  
  
## <a name="see-also"></a>См. также:
[Функция RAND &#40; Transact-SQL &#41;](../../t-sql/functions/rand-transact-sql.md)
  
  
