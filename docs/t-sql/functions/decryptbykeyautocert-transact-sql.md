---
description: DECRYPTBYKEYAUTOCERT (Transact-SQL)
title: DECRYPTBYKEYAUTOCERT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/09/2015
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DECRYPTBYKEYAUTOCERT
- DECRYPTBYKEYAUTOCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DECRYPTBYKEYAUTOCERT function
ms.assetid: 6b45fa2e-ffaa-46f7-86ff-5624596eda4a
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e45c856ee8ce1942840f47f5878de57525426c94
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96116329"
---
# <a name="decryptbykeyautocert-transact-sql"></a>DECRYPTBYKEYAUTOCERT (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Эта функция расшифровывает данные с помощью симметричного ключа. Симметричный ключ автоматически расшифровывается с помощью сертификата.  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
DecryptByKeyAutoCert ( cert_ID , cert_password   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }   
  [ , { authenticator | @authenticator } ] ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *cert_ID*  
Идентификатор сертификата, используемого для защиты симметричного ключа. *cert_ID* имеет тип данных **int**.  
  
*cert_password*  
Пароль, используемый для шифрования закрытого ключа сертификата. Может иметь значение `NULL`, если главный ключ базы данных защищает закрытый ключ. *cert_password* имеет тип данных **nvarchar**.  

'*ciphertext*'  
Строка данных, зашифрованная с помощью ключа. *ciphertext* имеет тип данных **varbinary**.  

@ciphertext  
Переменная типа **varbinary**, содержащая данные, зашифрованные с помощью ключа.  

*add_authenticator*  
Указывает, включен ли исходный процесс шифрования и зашифрована ли структура проверки подлинности вместе с данными в виде открытого текста. Значение должно соответствовать значению, переданному функции [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md) во время шифрования данных. *add_authenticator* имеет значение 1, если в процессе шифрования использовалась структура проверки подлинности. *add_authenticator* имеет тип данных **int**.  
  
@add_authenticator  
Переменная, указывающая, включен ли исходный процесс шифрования и зашифрована ли структура проверки подлинности вместе с данными в виде открытого текста. Значение должно соответствовать значению, переданному функции [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md) во время шифрования данных. *\@add_authenticator* имеет тип данных **int**.  
  
*authenticator*  
Данные, используемые в качестве основы для создания структуры проверки подлинности. Значение должно соответствовать значению, заданному функции [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md). *authenticator* имеет тип данных **sysname**.  
  
@authenticator  
Переменная, содержащая данные, из которых формируется структура проверки подлинности. Значение должно соответствовать значению, заданному функции [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md). *\@authenticator* имеет тип данных **sysname**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
Переменная типа **varbinary** с максимальным размером 8000 байт.  
  
## <a name="remarks"></a>Remarks  
Функция `DECRYPTBYKEYAUTOCERT` объединяет функциональность `OPEN SYMMETRIC KEY` и `DECRYPTBYKEY`. За одну операцию она сначала расшифровывает симметричный ключ, а затем с его помощью расшифровывает зашифрованный текст.  
  
## <a name="permissions"></a>Разрешения  
Необходимо разрешение `VIEW DEFINITION` для симметричного ключа и разрешение `CONTROL` для сертификата.   
  
## <a name="examples"></a>Примеры  
В этом примере показано, как `DECRYPTBYKEYAUTOCERT` может упростить код расшифровки. Этот код должен быть выполнен в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], для которой еще не задан главный ключ базы данных.  
  
```sql  
--Create the keys and certificate.  
USE AdventureWorks2012;  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'mzkvdlk979438teag$$ds987yghn)(*&4fdg^';  
OPEN MASTER KEY DECRYPTION BY PASSWORD = 'mzkvdlk979438teag$$ds987yghn)(*&4fdg^';  
CREATE CERTIFICATE HumanResources037   
   WITH SUBJECT = 'Sammamish HR',   
   EXPIRY_DATE = '10/31/2009';  
CREATE SYMMETRIC KEY SSN_Key_01 WITH ALGORITHM = DES  
    ENCRYPTION BY CERTIFICATE HumanResources037;  
GO  
----Add a column of encrypted data.  
ALTER TABLE HumanResources.Employee  
    ADD EncryptedNationalIDNumber varbinary(128);   
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037 ;  
UPDATE HumanResources.Employee  
SET EncryptedNationalIDNumber  
    = EncryptByKey(Key_GUID('SSN_Key_01'), NationalIDNumber);  
GO  
--  
--Close the key used to encrypt the data.  
CLOSE SYMMETRIC KEY SSN_Key_01;  
--  
--There are two ways to decrypt the stored data.  
--  
--OPTION ONE, using DecryptByKey()  
--1. Open the symmetric key  
--2. Decrypt the data  
--3. Close the symmetric key  
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037;  
SELECT NationalIDNumber, EncryptedNationalIDNumber    
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKey(EncryptedNationalIDNumber))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
CLOSE SYMMETRIC KEY SSN_Key_01;  
--  
--OPTION TWO, using DecryptByKeyAutoCert()  
SELECT NationalIDNumber, EncryptedNationalIDNumber   
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKeyAutoCert ( cert_ID('HumanResources037') , NULL ,EncryptedNationalIDNumber))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
```  
  
## <a name="see-also"></a>См. также  
 [OPEN SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [ENCRYPTBYKEY (Transact-SQL)](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [DECRYPTBYKEY (Transact-SQL)](../../t-sql/functions/decryptbykey-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
