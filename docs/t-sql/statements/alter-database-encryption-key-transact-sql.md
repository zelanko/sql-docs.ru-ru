---
description: ALTER DATABASE ENCRYPTION KEY (Transact-SQL)
title: ALTER DATABASE ENCRYPTION KEY (Transact-SQL) | Документы Майкрософт
ms.date: 04/16/2018
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER_DATABASE_ENCRYPTION_KEY_TSQL
- ALTER DATABASE ENCRYPTION
- ALTER_DATABASE_ENCRYPTION_TSQL
- ALTER DATABASE ENCRYPTION KEY
dev_langs:
- TSQL
helpviewer_keywords:
- database encryption key, alter
- ALTER DATABASE ENCRYPTION KEY
ms.assetid: f88dac4b-efe0-47ed-9808-972a4381377e
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = azuresqldb-mi-current || >= sql-server-2016 || >= sql-server-linux-2017 || = sqlallproducts-allversions||=azure-sqldw-latest
ms.openlocfilehash: b7a9573f1700c1a8912e075aaa732492ed89a9a9
ms.sourcegitcommit: ac9feb0b10847b369b77f3c03f8200c86ee4f4e0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/16/2020
ms.locfileid: "90688314"
---
# <a name="alter-database-encryption-key-transact-sql"></a>ALTER DATABASE ENCRYPTION KEY (Transact-SQL)
[!INCLUDE [sql-asa-pdw](../../includes/applies-to-version/sql-asa-pdw.md)]

  Изменяет ключ шифрования и сертификат, используемый для прозрачного шифрования базы данных. Дополнительные сведения о прозрачном шифровании баз данных см. в статье [Прозрачное шифрование данных (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
-- Syntax for SQL Server  
  
ALTER DATABASE ENCRYPTION KEY  
      REGENERATE WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   |  
   ENCRYPTION BY SERVER   
    {  
        CERTIFICATE Encryptor_Name |  
        ASYMMETRIC KEY Encryptor_Name  
    }  
[ ; ]  
```
  
> [!Note]
> [!INCLUDE [Synapse preview note](../../includes/synapse-preview-note.md)]
  
```syntaxsql
-- Syntax for Azure Synapse Analytics and Parallel Data Warehouse  
  
ALTER DATABASE ENCRYPTION KEY  
    {  
      {  
        REGENERATE WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
        [ ENCRYPTION BY SERVER CERTIFICATE Encryptor_Name ]  
      }  
      |  
      ENCRYPTION BY SERVER   CERTIFICATE Encryptor_Name    
    }  
[ ; ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 REGENERATE WITH ALGORITHM = { AES_128 \| AES_192 \| AES_256 \| TRIPLE_DES_3KEY }  
 Определяет алгоритм шифрования, который используется для ключа шифрования.  
  
 ENCRYPTION BY SERVER CERTIFICATE *Encryptor_Name*  
 Имя сертификата, используемого для шифрования ключа шифрования базы данных.  
  
 ENCRYPTION BY SERVER ASYMMETRIC KEY Encryptor_Name  
 Указывает имя асимметричного ключа, используемого для шифрования ключа шифрования базы данных.  
  
## <a name="remarks"></a>Remarks  
 Сертификат или асимметричный ключ, который используется для шифрования ключа шифрования базы данных, должен находиться в системной базе данных master.  
  
 Нет необходимости повторно создавать ключ шифрования базы данных, когда меняется владелец базы данных (dbo).
  
 После двукратного изменения ключа шифрования базы данных необходимо выполнить резервное копирование журнала перед следующим изменением ключа шифрования базы данных.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение CONTROL на базу данных и разрешение VIEW DEFINITION на сертификат или асимметричный ключ, используемый при шифровании ключа шифрования базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере ключ шифрования базы данных изменяется для использования алгоритма `AES_256`.  
  
```sql  
-- Uses AdventureWorks  
  
ALTER DATABASE ENCRYPTION KEY  
REGENERATE WITH ALGORITHM = AES_256;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Прозрачное шифрование данных (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [Шифрование SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [Ключи шифрования базы данных и SQL Server (ядро СУБД)](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE DATABASE ENCRYPTION KEY (Transact-SQL)](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY (Transact-SQL)](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)   
 [sys.dm_database_encryption_keys (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)  
  
  

