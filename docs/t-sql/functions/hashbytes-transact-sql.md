---
title: "HASHBYTES (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/29/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- HASHBYTES_TSQL
- HASHBYTES
dev_langs:
- TSQL
helpviewer_keywords:
- hash input
- HASHBYTES
ms.assetid: 0ea6a4d1-313e-4f70-b939-dd2cd570f6d6
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4826936736685a46e8df8604339a7d4a878981ee
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="hashbytes-transact-sql"></a>HASHBYTES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает хэш MD2, MD4, MD5, SHA1 или SHA2 входного значения в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HASHBYTES ( '<algorithm>', { @input | 'input' } )  
  
<algorithm>::= MD2 | MD4 | MD5 | SHA | SHA1 | SHA2_256 | SHA2_512   
```  
  
## <a name="arguments"></a>Аргументы  
 **"**\<алгоритм >**"**  
 Указывает используемый алгоритм хэширования. Этот аргумент обязателен и не имеет значения по умолчанию. Указание одинарных кавычек (") также обязательно. Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], все алгоритмы, отличные от SHA2_256 и SHA2_512 являются устаревшими. Старые алгоритмы (не рекомендуется) будут продолжать работать, но они будут вызывать событие устаревания.  
  
 **@input**  
 Указывает переменную, содержащую хэшируемые данные. **@input**— **varchar**, **nvarchar**, или **varbinary**.  
  
 **"** *ввода* **"**  
 Определяет выражение, анализирующее тип хэшируемых данных (символьная или двоичная строка).  
  
 Выходные данные соответствуют стандарту алгоритма: 128 бит (16 байт) для MD2, MD4 и MD5; 160 бит (20 байт) для SHA и SHA1; 256 бит (32 байта) для SHA2_256 и 512 бит (64 байта) для SHA2_512.  
  
**Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и более ранних версиях допускается входных значений ограничен 8000 байт.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **varbinary** (более 8000 байт)  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-return-the-hash-of-a-variable"></a>А. Возвращение хэша переменной  
 В следующем примере возвращается `SHA1` хэш **nvarchar** данные, хранящиеся в переменной `@HashThis`.  
  
```  
DECLARE @HashThis nvarchar(4000);  
SET @HashThis = CONVERT(nvarchar(4000),'dslfdkjLK85kldhnv$n000#knf');  
SELECT HASHBYTES('SHA1', @HashThis);  
  
```  
  
### <a name="b-return-the-hash-of-a-table-column"></a>Б. Возвращение хэша столбца таблицы  
 Следующий пример возвращает хэш SHA1 значений в столбце `c1` таблицы `Test1`.  
  
```  
CREATE TABLE dbo.Test1 (c1 nvarchar(50));  
INSERT dbo.Test1 VALUES ('This is a test.');  
INSERT dbo.Test1 VALUES ('This is test 2.');  
SELECT HASHBYTES('SHA1', c1) FROM dbo.Test1;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
-------------------------------------------  
0x0E7AAB0B4FF0FD2DFB4F0233E2EE7A26CD08F173  
0xF643A82F948DEFB922B12E50B950CEE130A934D6  
  
(2 row(s) affected)  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Выбор алгоритма шифрования](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
  

