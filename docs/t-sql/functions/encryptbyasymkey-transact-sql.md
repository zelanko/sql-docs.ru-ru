---
title: ENCRYPTBYASYMKEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ENCRYPTBYASYMKEY
- ENCRYPTBYASYMKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ENCRYPTBYASYMKEY function
- encryption [SQL Server], asymmetric keys
- asymmetric keys [SQL Server], ENCRYPTBYASYMKEY function
ms.assetid: 86bb2588-ab13-4db2-8f3c-42c9f572a67b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 3510c94a80f0ba7cf06817afd62d6d29e1878f1e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65948910"
---
# <a name="encryptbyasymkey-transact-sql"></a>ENCRYPTBYASYMKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Эта функция шифрует данные с помощью асимметричного ключа.  
  
 ![Значок ссылки на статью](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на статью") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
EncryptByAsymKey ( Asym_Key_ID , { 'plaintext' | @plaintext } )  
```  
  
## <a name="arguments"></a>Аргументы  
*asym_key_ID*  
Идентификатор асимметричного ключа в базе данных. *asym_key_ID* имеет тип данных **int**.  
  
*cleartext*  
Строка данных, которую функция `ENCRYPTBYASYMKEY` зашифрует с помощью асимметричного ключа. Аргумент *cleartext* может иметь тип данных
 
+ **binary**
+ **char**
+ **nchar**
+ **nvarchar**
+ **varbinary**
  
или диспетчер конфигурации служб
  
+ **varchar**
 
.  
  
**@plaintext**  
Переменная, содержащая значение, которое функция `ENCRYPTBYASYMKEY` зашифрует с помощью асимметричного ключа. **@plaintext** может иметь тип данных
  
+ **binary**
+ **char**
+ **nchar**
+ **nvarchar**
+ **varbinary**
  
или диспетчер конфигурации служб
  
+ **varchar**
 
.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
Переменная типа **varbinary** с максимальным размером 8000 байт.  
  
## <a name="remarks"></a>Remarks  
Операции шифрования и расшифровки с асимметричными ключами потребляют много ресурсов и потому становятся более затратными, чем при использовании симметричных ключей. При работе с большими наборами данных (например, с данными пользователей, хранящимися в таблицах базы данных) разработчикам не рекомендуется использовать асимметричный ключ для шифрования или расшифровки. Вместо этого рекомендуется сначала шифровать данные с помощью надежного симметричного ключа, а затем шифровать симметричный ключ с помощью асимметричного.  
  
В зависимости от алгоритма функция `ENCRYPTBYASYMKEY` возвращает значение **NULL**, если ввод превышает определенное число байтов. Ограничения:

+ С помощью 512-битового ключа RSA можно шифровать до 53 байт.
+ С помощью 1024-битового ключа можно шифровать до 117 байт.
+ С помощью 2048-битового ключа можно шифровать до 245 байт.

В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и сертификаты, и асимметричные ключи служат оболочками для ключей RSA.  
  
## <a name="examples"></a>Примеры  
В приведенном ниже примере текст из переменной `@cleartext` шифруется асимметричным ключом `JanainaAsymKey02`. Инструкция вставляет зашифрованные данные в таблицу `ProtectedData04`.  
  
```  
INSERT INTO AdventureWorks2012.Sales.ProtectedData04   
    VALUES( N'Data encrypted by asymmetric key ''JanainaAsymKey02''',  
    EncryptByAsymKey(AsymKey_ID('JanainaAsymKey02'), @cleartext) );  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [DECRYPTBYASYMKEY (Transact-SQL)](../../t-sql/functions/decryptbyasymkey-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  