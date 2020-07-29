---
title: DECRYPTBYPASSPHRASE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e2998d9ff84d7902095620e2e7949985adc3a6b0
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87113005"
---
# <a name="decryptbypassphrase-transact-sql"></a>DECRYPTBYPASSPHRASE (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Эта функция расшифровывает данные, изначально зашифрованные с помощью парольной фразы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
DecryptByPassPhrase ( { 'passphrase' | @passphrase }   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }  
    , { authenticator | @authenticator } ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *passphrase*  
Парольная фраза, использовавшаяся для формирования ключа шифрования.  
  
 @passphrase  
Переменная типа **char**, **nchar**, **nvarchar** или **varchar** с парольной фразой, использовавшейся для формирования ключа расшифровки.  
  
'*ciphertext*'  
Строка данных, зашифрованная с помощью ключа. *ciphertext* имеет тип данных **varbinary**.  
 
@ciphertext  
Переменная типа **varbinary**, содержащая данные, зашифрованные с помощью ключа. Переменная *\@ciphertext* обладает максимальным размером 8000 байт.  
  
*add_authenticator*  
Указывает, включен ли исходный процесс шифрования и зашифрована ли структура проверки подлинности вместе с данными в виде открытого текста. *add_authenticator* имеет значение 1, если в процессе шифрования использовалась структура проверки подлинности. *add_authenticator* имеет тип данных **int**.  
  
@add_authenticator  
Переменная, указывающая, включен ли исходный процесс шифрования и зашифрована ли структура проверки подлинности вместе с данными в виде открытого текста. Здесь *\@add_authenticator* имеет значение 1, если в процессе шифрования использовалась структура проверки подлинности. *\@add_authenticator* имеет тип данных **int**.  

*authenticator*  
Данные, используемые в качестве основы для создания структуры проверки подлинности. *authenticator* имеет тип данных **sysname**.  
  
@authenticator  
Переменная, содержащая данные, которые использовались в качестве основы для создания структуры проверки подлинности. *\@authenticator* имеет тип данных **sysname**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
Переменная типа **varbinary** с максимальным размером 8000 байт.  
  
## <a name="remarks"></a>Remarks  
Для выполнения `DECRYPTBYPASSPHRASE` разрешения не требуются. Функция `DECRYPTBYPASSPHRASE` возвращает значение NULL, если получает неправильную парольную фразу или данные структуры проверки подлинности.  
  
Функция `DECRYPTBYPASSPHRASE` использует парольную фразу для формирования ключа расшифровки. Этот ключ расшифровки не сохраняется.  
  
Если в зашифрованный текст включалась структура проверки подлинности, функция `DECRYPTBYPASSPHRASE` должна получить эту структуру во время расшифровки. Если значение структуры проверки подлинности, предоставленное для процесса расшифровки, не соответствует значению структуры проверки подлинности, изначально использовавшемуся для шифрования данных, операция `DECRYPTBYPASSPHRASE` завершится неудачно.  
  
## <a name="examples"></a>Примеры  
В приведенном ниже примере расшифровывается запись, обновленная в функции [EncryptByPassPhrase](../../t-sql/functions/encryptbypassphrase-transact-sql.md).  
  
```  
USE AdventureWorks2012;  
-- Get the passphrase from the user.  
DECLARE @PassphraseEnteredByUser nvarchar(128);  
SET @PassphraseEnteredByUser   
= 'A little learning is a dangerous thing!';  
  
-- Decrypt the encrypted record.  
SELECT CardNumber, CardNumber_EncryptedbyPassphrase   
    AS 'Encrypted card number', CONVERT(varchar,  
    DecryptByPassphrase(@PassphraseEnteredByUser, CardNumber_EncryptedbyPassphrase, 1   
    , CONVERT(varbinary, CreditCardID)))  
    AS 'Decrypted card number' FROM Sales.CreditCard   
    WHERE CreditCardID = '3681';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Выбор алгоритма шифрования](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [ENCRYPTBYPASSPHRASE (Transact-SQL)](../../t-sql/functions/encryptbypassphrase-transact-sql.md)  
  
  
