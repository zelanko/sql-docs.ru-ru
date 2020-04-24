---
title: DECRYPTBYASYMKEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: eae1442ce3e113e4e573218b8ee018b86c0f636f
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81631305"
---
# <a name="decryptbyasymkey-transact-sql"></a>DECRYPTBYASYMKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Эта функция расшифровывает зашифрованные данные с помощью асимметричного ключа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
DecryptByAsymKey (Asym_Key_ID , { 'ciphertext' | @ciphertext }   
    [ , 'Asym_Key_Password' ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Asym_Key_ID*  
Идентификатор асимметричного ключа в базе данных. *Asym_Key_ID* имеет тип данных **int**.  
  
 *ciphertext*  
Строка данных, зашифрованная с помощью асимметричного ключа.  
  
 @ciphertext  
Переменная типа **varbinary**, содержащая данные, зашифрованные с помощью асимметричного ключа.  
  
 *Asym_Key_Password*  
Пароль, используемый для шифрования асимметричного ключа в базе данных.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
Переменная типа **varbinary** с максимальным размером 8000 байт.  
  
## <a name="remarks"></a>Remarks  
По сравнению с симметричным шифрованием или расшифровкой шифрование или расшифровка с помощью асимметричного ключа является более дорогостоящей. При работе с большими наборами данных (например, с данными пользователей, хранящимися в таблицах) разработчикам не рекомендуется использовать асимметричный ключ для шифрования или расшифровки.  
  
## <a name="permissions"></a>Разрешения  
`DECRYPTBYASYMKEY` требуется разрешение CONTROL на асимметричный ключ.  
  
## <a name="examples"></a>Примеры  
В этом примере расшифровывается зашифрованный текст, изначально зашифрованный с помощью асимметричного ключа `JanainaAsymKey02`. Этот асимметричный ключ хранится в таблице `AdventureWorks2012.ProtectedData04`. В этом примере возвращаемые данные расшифровываются с помощью асимметричного ключа `JanainaAsymKey02`. Для расшифровки асимметричного ключа используется пароль `pGFD4bb925DGvbd2439587y`. Возвращаемый открытый текст приводится к типу **nvarchar**.  
  
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
 [ENCRYPTBYASYMKEY (Transact-SQL)](../../t-sql/functions/encryptbyasymkey-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [DROP ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)   
 [Выбор алгоритма шифрования](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
