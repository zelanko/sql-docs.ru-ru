---
title: HASHBYTES (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 20e5e1a2f85d81a49072fba1e6acae3bc9b1dc1e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33052731"
---
# <a name="hashbytes-transact-sql"></a>HASHBYTES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает хэш MD2, MD4, MD5, SHA1 или SHA2 входного значения в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HASHBYTES ( '<algorithm>', { @input | 'input' } )  
  
<algorithm>::= MD2 | MD4 | MD5 | SHA | SHA1 | SHA2_256 | SHA2_512   
```  
  
## <a name="arguments"></a>Аргументы  
 **'**\<algorithm>**'**  
 Указывает используемый алгоритм хэширования. Этот аргумент обязателен и не имеет значения по умолчанию. Указание одинарных кавычек (") также обязательно. Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] все алгоритмы, отличные от SHA2_256 и SHA2_512, являются нерекомендуемыми. Старые алгоритмы (нерекомендуемые) по-прежнему будут работать, но будут вызывать событие нерекомендуемого алгоритма.  
  
 **@input**  
 Указывает переменную, содержащую хэшируемые данные. **@input** имеет тип **varchar**, **nvarchar** или **varbinary**.  
  
 **'** *input* **'**  
 Определяет выражение, анализирующее тип хэшируемых данных (символьная или двоичная строка).  
  
 Выходные данные соответствуют стандарту алгоритма: 128 бит (16 байт) для MD2, MD4 и MD5; 160 бит (20 байт) для SHA и SHA1; 256 бит (32 байта) для SHA2_256 и 512 бит (64 байта) для SHA2_512.  
  
**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и более ранних версий допустимый размер входных значений ограничен 8000 байтами.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **varbinary** (не более 8000 байт)  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-return-the-hash-of-a-variable"></a>А. Возвращение хэша данных в переменной  
 В приведенном ниже примере возвращается хэш `SHA1` данных типа **nvarchar**, хранящихся в переменной `@HashThis`.  
  
```  
DECLARE @HashThis nvarchar(4000);  
SET @HashThis = CONVERT(nvarchar(4000),'dslfdkjLK85kldhnv$n000#knf');  
SELECT HASHBYTES('SHA1', @HashThis);  
  
```  
  
### <a name="b-return-the-hash-of-a-table-column"></a>Б. Получение хэша данных в столбце таблицы  
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
  
  
