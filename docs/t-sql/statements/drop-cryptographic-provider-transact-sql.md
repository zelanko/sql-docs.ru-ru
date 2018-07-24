---
title: DROP CRYPTOGRAPHIC PROVIDER (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP CRYPTOGRAPHIC PROVIDER
- DROP_CRYPTOGRAPHIC_PROVIDER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP CRYPTOGRAPHIC PROVIDER statement
ms.assetid: 71c55c20-439e-4897-aef5-f20e556d668f
caps.latest.revision: 12
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 642e402a103e207111b5f8b38703337920f5e164
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37974051"
---
# <a name="drop-cryptographic-provider-transact-sql"></a>DROP CRYPTOGRAPHIC PROVIDER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет поставщика служб шифрования из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP CRYPTOGRAPHIC PROVIDER provider_name   
```  
  
## <a name="arguments"></a>Аргументы  
 *provider_name*  
 Имя поставщика расширенного управления ключами.  
  
## <a name="remarks"></a>Примечания  
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
  
## <a name="see-also"></a>См. также  
 [Расширенное управление ключами (EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER (Transact-SQL)](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [ALTER CRYPTOGRAPHIC PROVIDER (Transact-SQL)](../../t-sql/statements/alter-cryptographic-provider-transact-sql.md)   
 [CREATE SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
  
