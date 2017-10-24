---
title: "DECRYPTBYASYMKEY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECRYPTBYASYMKEY
- DECRYPTBYASYMKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- asymmetric keys [SQL Server], DECRYPTBYASYMKEY function
- DECRYPTBYASYMKEY function
- decryption [SQL Server], asymmetric keys
ms.assetid: d9ebcd30-f01c-4cfe-b95e-ffe6ea13788b
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c7196e7eedf5d1a808853df55259fcee1891c345
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="decryptbyasymkey-transact-sql"></a>DECRYPTBYASYMKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Дешифрует данные асимметричным ключом.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DecryptByAsymKey (Asym_Key_ID , { 'ciphertext' | @ciphertext }   
    [ , 'Asym_Key_Password' ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Asym_Key_ID*  
 Идентификатор асимметричного ключа в базе данных. *Asym_Key_ID* — **int**.  
  
 *зашифрованный текст*  
 Строка данных, которая была зашифрована асимметричным ключом.  
  
 @ciphertext  
 Переменная типа **varbinary** , содержащий данные, которые были зашифрованы с помощью асимметричного ключа.  
  
 *Asym_Key_Password*  
 Пароль, который был использован при шифровке асимметричного ключа в базе данных.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **varbinary** с максимальным размером 8 000 байт.  
  
## <a name="remarks"></a>Замечания  
 Шифрование и дешифрование асимметричным ключом являются очень дорогостоящими по сравнению с шифрованием и дешифрованием симметричным ключом. Рекомендуется использовать асимметричный ключ при работе с большими наборами данных, например с данными пользователей в таблицах.  
  
## <a name="permissions"></a>Permissions  
 Требуется разрешение CONTROL на асимметричный ключ.  
  
## <a name="examples"></a>Примеры  
 Следующий пример расшифровывает текст, зашифрованный асимметричным ключом `JanainaAsymKey02`, хранящимся в таблице `AdventureWorks2012.ProtectedData04`. Возвращаемые данные зашифрованы асимметричным ключом `JanainaAsymKey02`, который был дешифрован паролем `pGFD4bb925DGvbd2439587y`. Открытый текст приводится к типу **nvarchar**.  
  
```  
SELECT CONVERT(nvarchar(max),  
    DecryptByAsymKey( AsymKey_Id('JanainaAsymKey02'),   
    ProtectedData, N'pGFD4bb925DGvbd2439587y' ))   
AS DecryptedData   
FROM [AdventureWorks2012].[Sales].[ProtectedData04]   
WHERE Description = N'encrypted by asym key''JanainaAsymKey02''';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ENCRYPTBYASYMKEY &#40; Transact-SQL &#41;](../../t-sql/functions/encryptbyasymkey-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [DROP ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)   
 [Выбор алгоритма шифрования](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

