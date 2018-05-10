---
title: DECRYPTBYPASSPHRASE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DECRYPTBYPASSPHRASE
- DECRYPTBYPASSPHRASE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- decryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], DECRYPTBYPASSPHRASE function
- DECRYPTBYPASSPHRASE function
ms.assetid: ca34b5cd-07b3-4dca-b66a-ed8c6a826c95
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 01e01348ab88ef33ab38a9fd9040d5ff0174cb26
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="decryptbypassphrase-transact-sql"></a>DECRYPTBYPASSPHRASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Расшифровывает данные, зашифрованные с помощью парольной фразы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DecryptByPassPhrase ( { 'passphrase' | @passphrase }   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }  
    , { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *passphrase*  
 Парольная фраза, которая будет использоваться при формировании ключа для расшифровки.  
  
 @passphrase  
 Переменная типа **nvarchar**, **char**, **varchar** или **nchar**, содержащая парольную фразу, которая будет использоваться при формировании ключа для расшифровки.  
  
 '*ciphertext*'  
 Зашифрованный текст, предназначенный для расшифровки.  
  
 @ciphertext  
 Переменная типа **varbinary**, содержащая зашифрованный текст. Максимальный размер 8 000 байт.  
  
 *add_authenticator*  
 Указывает, была ли структура проверки подлинности зашифровано вместе с неформатированным текстом. Имеет значение 1, если было использована структура проверки подлинности. **int**.  
  
 @add_authenticator  
 Указывает, была ли структура проверки подлинности зашифровано вместе с неформатированным текстом. Имеет значение 1, если было использована структура проверки подлинности. **int**.  
  
 *authenticator*  
 Данные структуры проверки подлинности. **sysname**.  
  
 @authenticator  
 Переменная, содержащая данные, на основе которых формируется структура проверки подлинности.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Переменная типа **varbinary** с максимальным размером 8000 байт.  
  
## <a name="remarks"></a>Remarks  
 Для выполнения этой функции разрешения не требуются.  
  
 Возвращает значения NULL, если используется неправильная парольная фраза или данные структуры проверки подлинности.  
  
 Парольная фраза используется при создания ключа для расшифровки, который не будет сохраняемым.  
  
 Если в зашифрованный текст включалась структура проверки подлинности, оно должно быть предоставлено во время расшифровки. Если значение структуры проверки подлинности, предоставленное во время расшифровки, не соответствует значению структуры проверки подлинности, зашифрованному вместе с данными, расшифровка завершится неудачно.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере расшифровывается запись, обновленная в функции [EncryptByPassPhrase](../../t-sql/functions/encryptbypassphrase-transact-sql.md).  
  
```  
USE AdventureWorks2012;  
-- Get the pass phrase from the user.  
DECLARE @PassphraseEnteredByUser nvarchar(128);  
SET @PassphraseEnteredByUser   
= 'A little learning is a dangerous thing!';  
  
-- Decrypt the encrypted record.  
SELECT CardNumber, CardNumber_EncryptedbyPassphrase   
    AS 'Encrypted card number', CONVERT(nvarchar,  
    DecryptByPassphrase(@PassphraseEnteredByUser, CardNumber_EncryptedbyPassphrase, 1   
    , CONVERT(varbinary, CreditCardID)))  
    AS 'Decrypted card number' FROM Sales.CreditCard   
    WHERE CreditCardID = '3681';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Выбор алгоритма шифрования](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [ENCRYPTBYPASSPHRASE (Transact-SQL)](../../t-sql/functions/encryptbypassphrase-transact-sql.md)  
  
  
