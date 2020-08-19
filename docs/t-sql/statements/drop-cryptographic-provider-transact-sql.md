---
description: DROP CRYPTOGRAPHIC PROVIDER (Transact-SQL)
title: DROP CRYPTOGRAPHIC PROVIDER (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP CRYPTOGRAPHIC PROVIDER
- DROP_CRYPTOGRAPHIC_PROVIDER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP CRYPTOGRAPHIC PROVIDER statement
ms.assetid: 71c55c20-439e-4897-aef5-f20e556d668f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 80c6b61bbded237a0eedb0ee39fc8d4a6f55700f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88416390"
---
# <a name="drop-cryptographic-provider-transact-sql"></a>DROP CRYPTOGRAPHIC PROVIDER (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет поставщика служб шифрования из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP CRYPTOGRAPHIC PROVIDER provider_name   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *provider_name*  
 Имя поставщика расширенного управления ключами.  
  
## <a name="remarks"></a>Комментарии  
 Чтобы удалить поставщик расширенного управления ключами, необходимо остановить все сеансы, в которых используется этот поставщик.  
  
 Поставщик расширенного управления ключами может быть удален только при условии отсутствия сопоставленных с ним учетных данных.  
  
 Если на момент удаления поставщика расширенного управления ключами существуют сопоставленные с ним ключи, идентификаторы GUID для этих ключей сохраняются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если впоследствии будет создан поставщик с теми же идентификаторами GUID для ключей, ключи могут быть использованы повторно.  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешение CONTROL на симметричный ключ.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется поставщик служб шифрования с именем `SecurityProvider`.  
  
```  
/* First, disable provider to perform the upgrade.  
This will terminate all open cryptographic sessions. */  
ALTER CRYPTOGRAPHIC PROVIDER SecurityProvider   
SET ENABLED = OFF;  
GO  
/* Drop the provider. */  
DROP CRYPTOGRAPHIC PROVIDER SecurityProvider;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенное управление ключами (EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [ALTER CRYPTOGRAPHIC PROVIDER (Transact-SQL)](../../t-sql/statements/alter-cryptographic-provider-transact-sql.md)   
 [CREATE SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
  
