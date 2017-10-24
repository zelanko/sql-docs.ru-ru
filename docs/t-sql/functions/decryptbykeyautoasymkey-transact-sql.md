---
title: "DECRYPTBYKEYAUTOASYMKEY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/09/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECRYPTBYKEYAUTOASYMKEY_TSQL
- DECRYPTBYKEYAUTOASYMKEY
dev_langs:
- TSQL
helpviewer_keywords:
- DECRYPTBYKEYAUTOASYMSKEY function
ms.assetid: 5521d4cf-740c-4ede-98b6-4ba90b84e32d
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 74aa8bad7e6d848296ef2997017758883226ac48
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="decryptbykeyautoasymkey-transact-sql"></a>DECRYPTBYKEYAUTOASYMKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Проводит расшифровку с применением симметричного ключа, который автоматически расшифровывается с помощью асимметричного ключа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DecryptByKeyAutoAsymKey ( akey_ID , akey_password   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }   
  [ , { authenticator | @authenticator } ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *akey_ID*  
 Идентификатор асимметричного ключа, используемого для защиты симметричного ключа. *akey_ID* — **int**.  
  
 *akey_password*  
 Пароль, защищающий закрытый ключ асимметричного ключа. Может принимать значение NULL, если закрытый ключ защищен главным ключом базы данных. *akey_password* — **nvarchar**.  
  
 "*зашифрованного текста*"  
 Данные, зашифрованные с помощью ключа. *зашифрованный текст* — **varbinary**.  
  
 @ciphertext  
 Переменная типа **varbinary** , содержащий данные, зашифрованные с помощью ключа.  
  
 *add_authenticator*  
 Указывает, была ли структура проверки подлинности зашифровано вместе с неформатированным текстом. Значение этого аргумента должно быть равно значению, переданному функции EncryptByKey при шифровании данных. Имеет значение 1, если было использована структура проверки подлинности. *add_authenticator* — **int**.  
  
 @add_authenticator  
 Указывает, была ли структура проверки подлинности зашифровано вместе с неформатированным текстом. Значение этого аргумента должно быть равно значению, переданному функции EncryptByKey при шифровании данных.  
  
 *Средство проверки подлинности*  
 Данные, из которых создается структура проверки подлинности. Значение аргумента должно совпадать со значением, заданным функции EncryptByKey. *Средство проверки подлинности* — **sysname**.  
  
 @authenticator  
 Переменная, содержащая сведения, из которых формируются данные для проверки подлинности. Значение аргумента должно совпадать со значением, заданным функции EncryptByKey.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **varbinary** с максимальным размером 8 000 байт.  
  
## <a name="remarks"></a>Замечания  
 DecryptByKeyAutoAsymKey сочетает функциональные возможности OPEN SYMMETRIC KEY и DecryptByKey. За одну операцию проводится расшифровка симметричного ключа и последующая расшифровка зашифрованного текста с его применением.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение VIEW DEFINITION на симметричный ключ и разрешение CONTROL на асимметричный ключ.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как с помощью функции `DecryptByKeyAutoAsymKey` можно упростить код, отвечающий за расшифровку. Этот код должен быть выполнен в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], для которой еще не задан главный ключ базы данных.  
  
```  
--Create the keys and certificate.  
USE AdventureWorks2012;  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'mzkvdMlk979438teag$$ds987yghn)(*&4fdg^';  
OPEN MASTER KEY DECRYPTION BY PASSWORD = 'mzkvdMlk979438teag$$ds987yghn)(*&4fdg^';  
CREATE ASYMMETRIC KEY SSN_AKey   
    WITH ALGORITHM = RSA_2048 ;   
GO  
CREATE SYMMETRIC KEY SSN_Key_02 WITH ALGORITHM = DES  
    ENCRYPTION BY ASYMMETRIC KEY SSN_AKey;  
GO  
--  
--Add a column of encrypted data.  
ALTER TABLE HumanResources.Employee  
    ADD EncryptedNationalIDNumber2 varbinary(128);   
OPEN SYMMETRIC KEY SSN_Key_02  
   DECRYPTION BY ASYMMETRIC KEY SSN_AKey;  
UPDATE HumanResources.Employee  
SET EncryptedNationalIDNumber2  
    = EncryptByKey(Key_GUID('SSN_Key_02'), NationalIDNumber);  
GO  
--Close the key used to encrypt the data.  
CLOSE SYMMETRIC KEY SSN_Key_02;  
--  
--There are two ways to decrypt the stored data.  
--  
--OPTION ONE, using DecryptByKey()  
--1. Open the symmetric key.  
--2. Decrypt the data.  
--3. Close the symmetric key.  
OPEN SYMMETRIC KEY SSN_Key_02  
   DECRYPTION BY ASYMMETRIC KEY SSN_AKey;  
SELECT NationalIDNumber, EncryptedNationalIDNumber2    
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKey(EncryptedNationalIDNumber2))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
CLOSE SYMMETRIC KEY SSN_Key_02;  
--  
--OPTION TWO, using DecryptByKeyAutoAsymKey()  
SELECT NationalIDNumber, EncryptedNationalIDNumber2   
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKeyAutoAsymKey ( AsymKey_ID('SSN_AKey') , NULL ,EncryptedNationalIDNumber2))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [OPEN SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [ENCRYPTBYKEY &#40; Transact-SQL &#41;](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [DECRYPTBYKEY &#40; Transact-SQL &#41;](../../t-sql/functions/decryptbykey-transact-sql.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

