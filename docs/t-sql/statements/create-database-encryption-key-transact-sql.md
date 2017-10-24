---
title: "Создание ключа ШИФРОВАНИЯ базы данных (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/24/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE_ENCRYPTION_KEY_TSQL
- ENCRYPTION_KEY_TSQL
- sql13.swb.dbencryptionkeyo.f1
- ENCRYPTION KEY
- DATABASE ENCRYPTION KEY
- CREATE_DATABASE_ENCRYPTION_KEY_TSQL
- CREATE DATABASE ENCRYPTION KEY
- sql13.swb.dbencryptionkeyg.f1
- CREATE DATABASE ENCRYPTION
- CREATE_DATABASE_ENCRYPTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database encryption key
- CREATE DATABASE ENCRYPTION KEY statement
- database encryption key, create
ms.assetid: 2ee95a32-5140-41bd-9ab3-a947b9990688
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 559e85cf5ba8e565a6afc86d3537b476365bd980
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-database-encryption-key-transact-sql"></a>CREATE DATABASE ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

 Создает ключ шифрования, используемый для прозрачного шифрования базы данных. Дополнительные сведения о прозрачном шифровании базы данных см. в разделе [прозрачное шифрование данных &#40; Прозрачное шифрование данных &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server  

CREATE DATABASE ENCRYPTION KEY  
       WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   ENCRYPTION BY SERVER   
    {  
        CERTIFICATE Encryptor_Name |  
        ASYMMETRIC KEY Encryptor_Name  
    }  
[ ; ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  

CREATE DATABASE ENCRYPTION KEY  
       WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
   ENCRYPTION BY SERVER CERTIFICATE Encryptor_Name   
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
WITH ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY }  
Определяет алгоритм шифрования, который используется для ключа шифрования.   
>  [!NOTE]
>    Начиная с SQL Server 2016, являются устаревшими все алгоритмы, отличные от AES_128, AES_192 и AES_256. Чтобы использовать старые алгоритмы (что не рекомендуется), необходимо установить уровень совместимости базы данных 120 или ниже.  
  
ENCRYPTION BY SERVER CERTIFICATE Encryptor_Name  
Имя шифратора, используемого для шифрования ключа шифрования базы данных.  
  
ENCRYPTION BY SERVER ASYMMETRIC KEY Encryptor_Name  
Указывает имя асимметричного ключа, используемого для шифрования ключа шифрования базы данных. Чтобы зашифровать ключ шифрования базы данных с помощью асимметричного ключа, используемый асимметричный ключ должен находиться в поставщике расширенного управления ключами.  
  
## <a name="remarks"></a>Замечания  
Ключ шифрования базы данных необходим базы данных могут быть зашифрованы с помощью *прозрачного шифрования базы данных* (TDE). При выполнении прозрачного шифрования базы данных вся база данных шифруется на уровне файлов без каких-либо специальных изменений кода. Сертификат или асимметричный ключ, который используется для шифрования ключа шифрования базы данных, должен находиться в системной базе данных master.  
  
Инструкции шифрования базы данных разрешены только для пользовательских баз данных.  
  
Ключ шифрования базы данных нельзя экспортировать из базы данных. Он доступен только для системы, пользователей, имеющих разрешение на отладку на сервере, и пользователей, имеющих доступ к сертификатам, с использованием которых выполняется шифрование и расшифровка ключа шифрования базы данных.  
  
Нет необходимости повторно создавать ключ шифрования базы данных, когда меняется владелец базы данных (dbo).  
  
Ключ шифрования базы данных создается автоматически для [!INCLUDE[ssSDS](../../includes/sssds-md.md)] базы данных. Необходимо создать с помощью инструкции CREATE DATABASE ENCRYPTION KEY.  
  
## <a name="permissions"></a>Permissions  
Требуется разрешение CONTROL на базу данных и разрешение VIEW DEFINITION на сертификат или асимметричный ключ, используемый при шифровании ключа шифрования базы данных.  
  
## <a name="examples"></a>Примеры  
Дополнительные примеры использования прозрачного шифрования данных см. в разделе [прозрачное шифрование данных &#40; Прозрачное шифрование данных &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md), [Включение прозрачного шифрования данных на SQL Server с помощью расширенного управления Ключами](../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md), и [расширенного управления ключами, с помощью хранилища ключей Azure &#40; SQL Server &#41; ](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
В следующем примере создается ключ шифрования базы данных с помощью алгоритма `AES_256` и защищается закрытый ключ с помощью сертификата с именем `MyServerCert`.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
Дополнительные примеры использования прозрачного шифрования данных см. в разделе [прозрачное шифрование данных (SQL Server PDW)](http://msdn.microsoft.com/en-us/b82ad21d-09dd-43dd-8fab-bcf2c8c3ac6d).  
  
В следующем примере создается ключ шифрования базы данных с помощью алгоритма `AES_256` и защищается закрытый ключ с помощью сертификата с именем `MyServerCert`.  
  
```  
-- Uses AdventureWorks  
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
[Прозрачное шифрование данных (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md)   
[Шифрование SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md)   
[Ключи шифрования базы данных и SQL Server (компонент Database Engine)](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
[Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
[Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
[ИЗМЕНИТЬ ключ ШИФРОВАНИЯ базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
[DROP DATABASE ENCRYPTION KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)   
[sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)  
    

