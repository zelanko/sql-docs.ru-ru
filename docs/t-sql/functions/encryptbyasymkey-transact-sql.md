---
description: ENCRYPTBYASYMKEY (Transact-SQL)
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
ms.openlocfilehash: 42ffb61535beefeee149124adf7873cce78c1535
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96128502"
---
# <a name="encryptbyasymkey-transact-sql"></a>ENCRYPTBYASYMKEY (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Эта функция шифрует данные с помощью асимметричного ключа.  
  
 ![Значок ссылки на статью](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на статью") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
EncryptByAsymKey ( Asym_Key_ID , { 'plaintext' | @plaintext } )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

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
  
или
  
+ **varchar**
 
.  
  
**\@plaintext**  
Переменная, содержащая значение, которое функция `ENCRYPTBYASYMKEY` зашифрует с помощью асимметричного ключа. Аргумент **\@plaintext** может иметь тип:
  
+ **binary**
+ **char**
+ **nchar**
+ **nvarchar**
+ **varbinary**
  
или
  
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
  
```sql  
INSERT INTO AdventureWorks2012.Sales.ProtectedData04   
    VALUES( N'Data encrypted by asymmetric key ''JanainaAsymKey02''',  
    EncryptByAsymKey(AsymKey_ID('JanainaAsymKey02'), @cleartext) );  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [DECRYPTBYASYMKEY (Transact-SQL)](../../t-sql/functions/decryptbyasymkey-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
