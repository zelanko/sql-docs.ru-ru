---
description: DROP ASYMMETRIC KEY (Transact-SQL)
title: DROP ASYMMETRIC KEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 49260a78ef3012f022a6d523bc2cc1d7ea1b128f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88478914"
---
# <a name="drop-asymmetric-key-transact-sql"></a>DROP ASYMMETRIC KEY (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Удаляет асимметричный ключ из текущей базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP ASYMMETRIC KEY key_name [ REMOVE PROVIDER KEY ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *key_name*  
 Имя асимметричного ключа, удаляемого из базы данных.  
  
 REMOVE PROVIDER KEY  
 Удаляет ключ расширенного управления ключами с устройства расширенного управления ключами. Дополнительные сведения о расширенном управлении ключами см. в разделе [Расширенное управление ключами (EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>Комментарии  
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
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [ALTER SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-symmetric-key-transact-sql.md)  
  
  
