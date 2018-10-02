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
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 773d575a65edaca18d76ba3e2109fe81bb20f88f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47819482"
---
# <a name="encryptbyasymkey-transact-sql"></a>ENCRYPTBYASYMKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Эта функция шифрует данные с помощью асимметричного ключа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
Операции шифрования и расшифровки с помощью асимметричного ключа могут потреблять много ресурсов и поэтому являются очень затратными по сравнению с шифрованием и расшифровкой с помощью симметричного ключа. При работе с большими наборами данных (например, с данными пользователей, хранящимися в таблицах базы данных) разработчикам не рекомендуется использовать асимметричный ключ для шифрования или расшифровки. Вместо этого рекомендуется сначала шифровать данные с помощью надежного симметричного ключа, а затем шифровать симметричный ключ с помощью асимметричного.  
  
В зависимости от алгоритма функция `ENCRYPTBYASYMKEY` возвращает значение **NULL**, если ввод превышает определенное число байтов. Ограничения:

+ с помощью 512-битного ключа RSA можно шифровать до 53 байт;
+ с помощью 1024-битного ключа можно шифровать до 117 байт;
+ с помощью 2048-битного ключа можно шифровать до 245 байт.

Обратите внимание, что в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и сертификаты, и асимметричные ключи служат оболочками для ключей RSA.  
  
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
 [CREATE ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
