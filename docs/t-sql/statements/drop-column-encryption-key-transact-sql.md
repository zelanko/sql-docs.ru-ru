---
title: DROP COLUMN ENCRYPTION KEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP COLUMN ENCRYPTION
- DROP COLUMN ENCRYPTION KEY
- DROP_COLUMN_ENCRYPTION_TSQL
- DROP_COLUMN_ENCRYPTION_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP COLUMN ENCRYPTION KEY statement
- column encryption key, drop
ms.assetid: 86415302-1383-4d36-9fc7-f780831a2d37
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 981ea3dd0f9b1b73f22293043f548ba9b990b0b7
ms.sourcegitcommit: 9c99f992abd5f1c174b3d1e978774dffb99ff218
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361534"
---
# <a name="drop-column-encryption-key-transact-sql"></a>DROP COLUMN ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Удаляет ключ шифрования столбца из базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP COLUMN ENCRYPTION KEY key_name [;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *key_name*  
 Имя, под которым ключ шифрования столбца будет удален из базы данных.  
  
## <a name="remarks"></a>Примечания  
 Ключ шифрования столбца невозможно удалить, если он используется для шифрования любого столбца в базе данных. Сначала следует удалить все столбцы, использующие ключ шифрования столбца.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение **ALTER ANY SYMMETRIC KEY** для базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-dropping-a-column-encryption-key"></a>A. Удаление ключа шифрования столбца  
 В следующем примере показано удаление ключа шифрования столбца с именем `MyCEK`.  
  
```  
DROP COLUMN ENCRYPTION KEY MyCEK;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [ALTER COLUMN ENCRYPTION KEY (Transact-SQL)](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)   
 [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md)  
  
  
