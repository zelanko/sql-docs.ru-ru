---
title: "DECRYPTBYKEYAUTOCERT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/09/2015
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECRYPTBYKEYAUTOCERT
- DECRYPTBYKEYAUTOCERT_TSQL
dev_langs: TSQL
helpviewer_keywords: DECRYPTBYKEYAUTOCERT function
ms.assetid: 6b45fa2e-ffaa-46f7-86ff-5624596eda4a
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9aca90f988ae2d12d9a7c26f01673530b1a07f4b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="decryptbykeyautocert-transact-sql"></a>DECRYPTBYKEYAUTOCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Расшифровка с помощью симметричного ключа, который автоматически расшифровывается с помощью сертификата.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DecryptByKeyAutoCert ( cert_ID , cert_password   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }   
  [ , { authenticator | @authenticator } ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *cert_ID*  
 Идентификатор сертификата, используемого для защиты симметричного ключа. *cert_ID* — **int**.  
  
 *cert_password*  
 Пароль, защищающий закрытый ключ сертификата. Может принимать значение NULL, если закрытый ключ защищен главным ключом базы данных. *cert_password* — **nvarchar**.  
  
 "*зашифрованного текста*"  
 Данные, зашифрованные с помощью ключа. *зашифрованный текст* — **varbinary**.  
  
 @ciphertext  
 Переменная типа **varbinary** , содержащий данные, зашифрованные с помощью ключа.  
  
 *add_authenticator*  
 Указывает, была ли структура проверки подлинности зашифровано вместе с неформатированным текстом. Должно быть равно значению, переданному функции EncryptByKey при шифровании данных. — **1** Если использовалась структура проверки подлинности. *add_authenticator* — **int**.  
  
 @add_authenticator  
 Указывает, была ли структура проверки подлинности зашифровано вместе с неформатированным текстом. Значение этого аргумента должно быть равно значению, переданному функции EncryptByKey при шифровании данных.  
  
 *Средство проверки подлинности*  
 Данные, из которых создается структура проверки подлинности. Значение аргумента должно совпадать со значением, заданным функции EncryptByKey. *Средство проверки подлинности* — **sysname**.  
  
 @authenticator  
 Переменная, содержащая сведения, из которых формируются данные для проверки подлинности. Значение аргумента должно совпадать со значением, заданным функции EncryptByKey.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **varbinary** с максимальным размером 8 000 байт.  
  
## <a name="remarks"></a>Замечания  
 Функция DecryptByKeyAutoCert объединяет функциональность OPEN SYMMETRIC KEY и DecryptByKey. В отдельной операции она расшифровывает симметричный ключ и использует его для расшифровки текста.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение VIEW DEFINITION на симметричный ключ и разрешение CONTROL на сертификат.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как с помощью функции `DecryptByKeyAutoCert` можно упростить код, отвечающий за расшифровку. Этот код должен быть выполнен в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], для которой еще не задан главный ключ базы данных.  
  
```  
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
  
## <a name="see-also"></a>См. также:  
 [OPEN SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [ENCRYPTBYKEY &#40; Transact-SQL &#41;](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [DECRYPTBYKEY &#40; Transact-SQL &#41;](../../t-sql/functions/decryptbykey-transact-sql.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
