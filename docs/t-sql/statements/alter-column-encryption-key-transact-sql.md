---
title: ALTER COLUMN ENCRYPTION KEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER COLUMN ENCRYPTION
- ALTER_COLUMN_ENCRYPTION_TSQL
- ALTER COLUMN ENCRYPTION KEY
- ALTER_COLUMN_ENCRYPTION_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column encryption key, alter
- ALTER COLUMN ENCRYPTION KEY statement
ms.assetid: c79a220d-e178-4091-a330-c924cc0f0ae0
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: c06fb5b28e1c3ec5bd50b8922bcdf1e5d1b27ff7
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "73594394"
---
# <a name="alter-column-encryption-key-transact-sql"></a>ALTER COLUMN ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Изменяет ключ шифрования столбца в базе данных, добавляя или удаляя зашифрованное значение. У ключа шифрования столбцов может быть до двух значений, что позволяет менять соответствующий главный ключ столбца. Ключ шифрования столбцов используется при шифровании столбцов с помощью [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md) или [Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves.md). Перед добавлением значения ключа шифрования столбцов необходимо определить главный ключ столбца, который использовался для шифрования значения, с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или инструкции [CREATE MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
ALTER COLUMN ENCRYPTION KEY key_name   
    [ ADD | DROP ] VALUE   
    (  
        COLUMN_MASTER_KEY = column_master_key_name   
        [, ALGORITHM = 'algorithm_name' , ENCRYPTED_VALUE =  varbinary_literal ]   
    ) [;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *key_name*  
 Ключ шифрования столбца, который требуется изменить.  
  
 *column_master_key_name*  
 Указывает имя главного ключа столбца (CMK), используемого для шифрования ключа шифрования столбца (CEK).  
  
 *algorithm_name*  
 Имя алгоритма шифрования значения. Для системных поставщиков это должен быть алгоритм **RSA_OAEP**. Этот аргумент является недопустимым при удалении значения ключа шифрования столбца.  
  
 *varbinary_literal*  
 Большой двоичный объект ключа CEK, зашифрованный с помощью указанного главного ключа шифрования. Этот аргумент является недопустимым при удалении значения ключа шифрования столбца.  
  
> [!WARNING]  
>  Никогда не передавайте значения ключа шифрования столбца в виде открытого текста в этой инструкции. Это является преимуществом этой функции.  
  
## <a name="remarks"></a>Remarks  
Как правило, ключ шифрования столбца создается со всего одним зашифрованным значением. Когда требуется сменить главный ключ столбца (заменить текущий главный ключ столбца новым), можно добавить новое значение ключа шифрования столбца, зашифрованное с помощью нового главного ключа столбца. Этот рабочий процесс позволяет удостовериться, что клиентские приложения смогут обращаться к данным, зашифрованным с помощью ключа шифрования, тогда как новый главный ключ столбца будет доступен для клиентских приложений. Драйвер с поддержкой Always Encrypted в клиентском приложении, не имеющем доступа к новому главному ключу, сможет использовать значение ключа шифрования столбца, зашифрованное с помощью старого главного ключа столбца, для доступа к конфиденциальным данным. Для алгоритмов шифрования, поддерживаемых функцией Always Encrypted, требуется значение открытого текста размером 256 бит. 
 
Для смены главных ключей столбцов рекомендуется использовать такие средства, как SQL Server Management Studio (SSMS) или PowerShell. См. статьи [Смена ключей Always Encrypted с помощью SQL Server Management Studio](../../relational-databases/security/encryption/rotate-always-encrypted-keys-using-ssms.md) и [Смена ключей Always Encrypted с помощью PowerShell](../../relational-databases/security/encryption/rotate-always-encrypted-keys-using-powershell.md).

Зашифрованное значение должно быть создано с помощью поставщика хранилища ключей, который инкапсулирует хранилище ключей, содержащее главный ключ столбца.  

 Главные ключи столбцов меняются по следующим причинам.
- Нормативные правила могут требовать периодической смены ключей.
- Главный ключ столбца скомпрометирован, и его нужно заменить по соображениям безопасности.
- Включение или отключение совместного использования ключей шифрования столбцов с безопасным анклавом на стороне сервера. Например, если текущий главный ключ столбца не поддерживает вычисления в анклаве (не определено со свойством ENCLAVE_COMPUTATIONS), а вы хотите включить вычисления в анклаве для столбцов, защищенных с помощью ключа шифрования столбца (который, в свою очередь, шифруется главным ключом), то вам необходимо поменять ключ шифрования столбца на новый со свойством ENCLAVE_COMPUTATIONS. [Общие сведения об управлении ключами для Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md) и [Управление ключами для Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md).

Сведения о ключах шифрования столбцов см. в разделах [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md), [sys.column_encryption_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md) и [sys.column_encryption_key_values (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение **ALTER ANY SYMMETRIC KEY** для базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-adding-a-column-encryption-key-value"></a>A. Добавление значения ключа шифрования столбца  
 В следующем примере показано изменение ключа шифрования столбца с именем `MyCEK`.  
  
```sql  
ALTER COLUMN ENCRYPTION KEY MyCEK  
ADD VALUE  
(  
    COLUMN_MASTER_KEY = MyCMK2,   
    ALGORITHM = 'RSA_OAEP',   
    ENCRYPTED_VALUE = 0x016E000001630075007200720065006E00740075007300650072002F006D0079002F0064006500650063006200660034006100340031003000380034006200350033003200360066003200630062006200350030003600380065003900620061003000320030003600610037003800310066001DDA6134C3B73A90D349C8905782DD819B428162CF5B051639BA46EC69A7C8C8F81591A92C395711493B25DCBCCC57836E5B9F17A0713E840721D098F3F8E023ABCDFE2F6D8CC4339FC8F88630ED9EBADA5CA8EEAFA84164C1095B12AE161EABC1DF778C07F07D413AF1ED900F578FC00894BEE705EAC60F4A5090BBE09885D2EFE1C915F7B4C581D9CE3FDAB78ACF4829F85752E9FC985DEB8773889EE4A1945BD554724803A6F5DC0A2CD5EFE001ABED8D61E8449E4FAA9E4DD392DA8D292ECC6EB149E843E395CDE0F98D04940A28C4B05F747149B34A0BAEC04FFF3E304C84AF1FF81225E615B5F94E334378A0A888EF88F4E79F66CB377E3C21964AACB5049C08435FE84EEEF39D20A665C17E04898914A85B3DE23D56575EBC682D154F4F15C37723E04974DB370180A9A579BC84F6BC9B5E7C223E5CBEE721E57EE07EFDCC0A3257BBEBF9ADFFB00DBF7EF682EC1C4C47451438F90B4CF8DA709940F72CFDC91C6EB4E37B4ED7E2385B1FF71B28A1D2669FBEB18EA89F9D391D2FDDEA0ED362E6A591AC64EF4AE31CA8766C259ECB77D01A7F5C36B8418F91C1BEADDD4491C80F0016B66421B4B788C55127135DA2FA625FB7FD195FB40D90A6C67328602ECAF3EC4F5894BFD84A99EB4753BE0D22E0D4DE6A0ADFEDC80EB1B556749B4A8AD00E73B329C95827AB91C0256347E85E3C5FD6726D0E1FE82C925D3DF4A9  
);  
GO  
  
```  
  
### <a name="b-dropping-a-column-encryption-key-value"></a>Б. Удаление значения ключа шифрования столбца  
 В следующем примере показано изменение ключа шифрования столбца с именем `MyCEK` путем удаления значения.  
  
```sql  
ALTER COLUMN ENCRYPTION KEY MyCEK  
DROP VALUE  
(  
    COLUMN_MASTER_KEY = MyCMK  
);  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [DROP COLUMN ENCRYPTION KEY (Transact-SQL)](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Постоянное шифрование (компонент Database Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_encryption_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)   
 [sys.column_encryption_key_values (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
 [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Общие сведения об управлении ключами для Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)   
 [Управление ключами для Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md)   
  
  
