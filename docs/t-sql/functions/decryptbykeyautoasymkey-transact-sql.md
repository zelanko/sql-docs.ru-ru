---
title: DECRYPTBYKEYAUTOASYMKEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/09/2015
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DECRYPTBYKEYAUTOASYMKEY_TSQL
- DECRYPTBYKEYAUTOASYMKEY
dev_langs:
- TSQL
helpviewer_keywords:
- DECRYPTBYKEYAUTOASYMSKEY function
ms.assetid: 5521d4cf-740c-4ede-98b6-4ba90b84e32d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 14668b9fac1ba05d458bdedc038faaf2883dc9c1
ms.sourcegitcommit: a24f6e12357979f1134a54a036ebc58049484a4f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71314570"
---
# <a name="decryptbykeyautoasymkey-transact-sql"></a>DECRYPTBYKEYAUTOASYMKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Эта функция расшифровывает зашифрованные данные. Для этого она сначала расшифровывает симметричный ключ с помощью отдельного асимметричного ключа, а затем расшифровывает зашифрованные данные с помощью симметричного ключа, извлеченного на первом шаге.  
  
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
Идентификатор асимметричного ключа, используемого для шифрования симметричного ключа. *akey_ID* имеет тип данных **int**.  
  
 *akey_password*  
Пароль, защищающий асимметричный ключ. *akey_password* может иметь значение NULL, если главный ключ базы данных защищает асимметричный закрытый ключ. *akey_password* имеет тип данных **nvarchar**.  
  
 *ciphertext* Данные, зашифрованные с помощью ключа. *ciphertext* имеет тип данных **varbinary**.  
  
 @ciphertext  
Переменная типа **varbinary**, содержащая данные, зашифрованные с помощью симметричного ключа.  
  
 *add_authenticator*  
Указывает, включен ли исходный процесс шифрования и зашифрована ли структура проверки подлинности вместе с данными в виде открытого текста. Значение должно соответствовать значению, переданному функции [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md) во время шифрования данных. *add_authenticator* имеет значение 1, если в процессе шифрования использовалась структура проверки подлинности. *add_authenticator* имеет тип данных **int**.  
  
 @add_authenticator  
Переменная, указывающая, включен ли исходный процесс шифрования и зашифрована ли структура проверки подлинности вместе с данными в виде открытого текста. Значение должно соответствовать значению, переданному функции [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md) во время шифрования данных. *\@add_authenticator* имеет тип данных **int**.
  
 *authenticator*  
Данные, используемые в качестве основы для создания структуры проверки подлинности. Значение должно соответствовать значению, заданному функции [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md). *authenticator* имеет тип данных **sysname**.  
  
 @authenticator  
Переменная, содержащая данные, из которых формируется структура проверки подлинности. Значение должно соответствовать значению, заданному функции [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md). *\@authenticator* имеет тип данных **sysname**.  
  
@add_authenticator  
Переменная, указывающая, включен ли исходный процесс шифрования и зашифрована ли структура проверки подлинности вместе с данными в виде открытого текста. Значение должно соответствовать значению, переданному функции [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md) во время шифрования данных. *\@add_authenticator* имеет тип данных **int**.  

*authenticator*  
Данные, используемые в качестве основы для создания структуры проверки подлинности. Значение должно соответствовать значению, заданному функции [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md). *authenticator* имеет тип данных **sysname**.

@authenticator  
Переменная, содержащая данные, из которых формируется структура проверки подлинности. Значение должно соответствовать значению, заданному функции [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md). *\@authenticator* имеет тип данных **sysname**.  

## <a name="return-types"></a>Типы возвращаемых данных  
Переменная типа **varbinary** с максимальным размером 8000 байт.  
  
## <a name="remarks"></a>Remarks  
Функция `DECRYPTBYKEYAUTOASYMKEY` объединяет функциональность `OPEN SYMMETRIC KEY` и `DECRYPTBYKEY`. За одну операцию она сначала расшифровывает симметричный ключ, а затем с его помощью расшифровывает зашифрованный текст.  
  
## <a name="permissions"></a>Разрешения  
Необходимо разрешение `VIEW DEFINITION` на симметричный ключ и разрешение `CONTROL` на асимметричный ключ.  
  
## <a name="examples"></a>Примеры
В этом примере показано, как `DECRYPTBYKEYAUTOASYMKEY` может упростить код расшифровки. Этот код должен быть выполнен в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], для которой еще не задан главный ключ базы данных.  

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
 [ENCRYPTBYKEY (Transact-SQL)](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [DECRYPTBYKEY (Transact-SQL)](../../t-sql/functions/decryptbykey-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
