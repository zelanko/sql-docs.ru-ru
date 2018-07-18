---
title: DROP ASYMMETRIC KEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP ASYMMETRIC KEY
- DROP_ASYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- asymmetric keys [SQL Server], removing
- removing asymmetric keys
- encryption [SQL Server], asymmetric keys
- DROP ASYMMETRIC KEY statement
- dropping asymmetric keys
- deleting asymmetric keys
- cryptography [SQL Server], asymmetric keys
ms.assetid: bf94ac07-9b62-4318-b55b-1eed8f3a1ac6
caps.latest.revision: 32
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 4bb266c52467a3f1b8d74bece16a0b2450c9efaa
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/04/2018
ms.locfileid: "37782165"
---
# <a name="drop-asymmetric-key-transact-sql"></a>DROP ASYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Удаляет асимметричный ключ из текущей базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP ASYMMETRIC KEY key_name [ REMOVE PROVIDER KEY ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *key_name*  
 Имя асимметричного ключа, удаляемого из базы данных.  
  
 REMOVE PROVIDER KEY  
 Удаляет с устройства поставщика расширенного управления ключами ключ поставщика расширенного управления ключами. Дополнительные сведения о расширенном управлении ключами см. в разделе [Расширенное управление ключами (EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>Примечания  
 Нельзя удалять асимметричный ключ, которым в базе данных зашифрован симметричный ключ или с которым сопоставлено имя входа. Прежде чем удалять такой ключ, следует сначала удалить пользователя или имя входа, с которым этот ключ сопоставлен, либо удалить или перешифровать симметричный ключ, который зашифрован данным асимметричным ключом. Для удаления шифрования, выполненного асимметричным ключом, предназначен параметр DROP ENCRYPTION инструкции [ALTER SYMMETRIC KEY](../../t-sql/statements/alter-symmetric-key-transact-sql.md).  
  
 Метаданные асимметричных ключей доступны через представление каталога [sys.asymmetric_keys](../../relational-databases/system-catalog-views/sys-asymmetric-keys-transact-sql.md). Сами ключи для просмотра из базы данных недоступны.  
  
 Если асимметричный ключ сопоставлен ключу поставщика расширенного управления ключами на устройстве поставщика, а параметр REMOVE PROVIDER KEY не указан, то ключ будет удален из базы данных, но не с устройства. Будет выдано предупреждение.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение CONTROL на асимметричный ключ.  
  
## <a name="examples"></a>Примеры  
 В следующем примере производится удаление асимметричного ключа `MirandaXAsymKey6` из базы данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
DROP ASYMMETRIC KEY MirandaXAsymKey6;  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [ALTER SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-symmetric-key-transact-sql.md)  
  
  
