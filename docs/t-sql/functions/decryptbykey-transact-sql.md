---
title: DECRYPTBYKEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DecryptByKey_TSQL
- DECRYPTBYKEY
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], DecryptByKey function
- decryption [SQL Server], keys
- decryption [SQL Server], symmetric keys
- DECRYPTBYKEY function
ms.assetid: 6edf121f-ac62-4dae-90e6-6938f32603c9
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 7f9e1e678fba7a2b2d24a85f4d57f1112b3d4cb8
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779480"
---
# <a name="decryptbykey-transact-sql"></a>DECRYPTBYKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Эта функция расшифровывает данные с помощью симметричного ключа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DecryptByKey ( { 'ciphertext' | @ciphertext }   
    [ , add_authenticator, { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>Аргументы  
*ciphertext*  
Переменная типа **varbinary**, содержащая данные, зашифрованные с помощью ключа.  
  
**@ciphertext**  
Переменная типа **varbinary**, содержащая данные, зашифрованные с помощью ключа.  
  
 *add_authenticator*  
Указывает, включен ли исходный процесс шифрования и зашифрована ли структура проверки подлинности вместе с данными в виде открытого текста. Значение должно соответствовать значению, переданному функции [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md) во время шифрования данных. *add_authenticator* имеет тип данных **int**.  
  
 *authenticator*  
Данные, используемые в качестве основы для создания структуры проверки подлинности. Значение должно соответствовать значению, заданному функции [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md). *authenticator* имеет тип данных **sysname**.  

**@authenticator**  
Переменная, содержащая данные, из которых формируется структура проверки подлинности. Значение должно соответствовать значению, заданному функции [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md). *@authenticator* имеет тип данных **sysname**.  

## <a name="return-types"></a>Типы возвращаемых данных  
Переменная типа **varbinary** с максимальным размером 8000 байт. `DECRYPTBYKEY` возвращает NULL, если симметричный ключ, используемый для шифрования данных, не является открытым или если *ciphertext* имеет значение NULL.  
  
## <a name="remarks"></a>Remarks  
`DECRYPTBYKEY` использует симметричный ключ. Этот ключ уже должен быть открыт в базе данных. `DECRYPTBYKEY` допускает несколько одновременно открытых ключей. Открывать ключ непосредственно перед расшифровкой зашифрованного текста необязательно.  
  
Симметричные шифрование и расшифровка обычно выполняются относительно быстро и хорошо подходят для операций, связанных с большими объемами данных.  
  
## <a name="permissions"></a>Разрешения  
Симметричный ключ уже должен быть открыт в текущем сеансе. Дополнительные сведения см. в статье [OPEN SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/open-symmetric-key-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-decrypting-by-using-a-symmetric-key"></a>A. Декодирование с помощью симметричного ключа  
В этом примере зашифрованный текст расшифровывается с помощью симметричного ключа.  
  
```  
-- First, open the symmetric key with which to decrypt the data.  
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037;  
GO  
  
-- Now list the original ID, the encrypted ID, and the   
-- decrypted ciphertext. If the decryption worked, the original  
-- and the decrypted ID will match.  
SELECT NationalIDNumber, EncryptedNationalID   
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKey(EncryptedNationalID))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
GO  
```  
  
### <a name="b-decrypting-by-using-a-symmetric-key-and-an-authenticating-hash"></a>Б. Декодирование с помощью симметричного ключа и цифровой подписи  
В этом примере расшифровываются данные, изначально зашифрованные вместе со структурой проверки подлинности.  
  
```  
-- First, open the symmetric key with which to decrypt the data  
OPEN SYMMETRIC KEY CreditCards_Key11  
   DECRYPTION BY CERTIFICATE Sales09;  
GO  
  
-- Now list the original card number, the encrypted card number,  
-- and the decrypted ciphertext. If the decryption worked,   
-- the original number will match the decrypted number.  
SELECT CardNumber, CardNumber_Encrypted   
    AS 'Encrypted card number', CONVERT(nvarchar,  
    DecryptByKey(CardNumber_Encrypted, 1 ,   
    HashBytes('SHA1', CONVERT(varbinary, CreditCardID))))   
    AS 'Decrypted card number' FROM Sales.CreditCard;  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [ENCRYPTBYKEY (Transact-SQL)](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [CREATE SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Выбор алгоритма шифрования](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
  
