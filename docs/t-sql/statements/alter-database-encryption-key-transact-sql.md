---
title: "ИЗМЕНИТЬ ключ ШИФРОВАНИЯ базы данных (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: c0ea8313662a84b71f665ac2402733aa15eaac7a
ms.contentlocale: ru-ru
ms.lasthandoff: 10/24/2017

---
# <a name="alter-database-encryption-key-transact-sql"></a>ALTER DATABASE ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Изменяет ключ шифрования и сертификат, используемый для прозрачного шифрования базы данных. Дополнительные сведения о прозрачном шифровании базы данных см. в разделе [прозрачное шифрование данных &#40; Прозрачное шифрование данных &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
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
  
## <a name="arguments"></a>Аргументы  
 REGENERATE WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
 Определяет алгоритм шифрования, который используется для ключа шифрования.  
  
 ШИФРОВАНИЕ по СЕРТИФИКАТУ сервера *Encryptor_Name*  
 Имя сертификата, используемого для шифрования ключа шифрования базы данных.  
  
 ENCRYPTION BY SERVER ASYMMETRIC KEY Encryptor_Name  
 Указывает имя асимметричного ключа, используемого для шифрования ключа шифрования базы данных.  
  
## <a name="remarks"></a>Замечания  
 Сертификат или асимметричный ключ, который используется для шифрования ключа шифрования базы данных, должен находиться в системной базе данных master.  
  
 Нет необходимости повторно создавать ключ шифрования базы данных, когда меняется владелец базы данных (dbo).  
  
 После двукратного изменения ключа шифрования базы данных необходимо выполнить резервное копирование журнала перед следующим изменением ключа шифрования базы данных.  
  
## <a name="permissions"></a>Permissions  
 Требуется разрешение CONTROL на базу данных и разрешение VIEW DEFINITION на сертификат или асимметричный ключ, используемый при шифровании ключа шифрования базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере ключ шифрования базы данных изменяется для использования алгоритма `AES_256`.  
  
```  
-- Uses AdventureWorks  
  
ALTER DATABASE ENCRYPTION KEY  
REGENERATE WITH ALGORITHM = AES_256;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Прозрачное шифрование данных (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [Шифрование SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [Ключи шифрования базы данных и SQL Server (компонент Database Engine)](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [СОЗДАТЬ ключ ШИФРОВАНИЯ базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)   
 [sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)  
  
  


