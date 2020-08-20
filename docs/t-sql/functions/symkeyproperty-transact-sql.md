---
description: SYMKEYPROPERTY (Transact-SQL)
title: SYMKEYPROPERTY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SYMKEYPROPERTY_TSQL
- SYMKEYPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- SYMKEYPROPERTY
ms.assetid: 3d1f7075-3a3c-4660-8cd0-ed938b86fecd
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 1bd4e00191e7200bcdd5c8d38ac7fa008eeda0dc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88479571"
---
# <a name="symkeyproperty-transact-sql"></a>SYMKEYPROPERTY (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает алгоритм симметричного ключа, созданный из модуля расширенного управления ключами.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SYMKEYPROPERTY ( Key_ID , 'algorithm_desc' | 'string_sid' | 'sid' )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *Key_ID*  
 Идентификатор Key_ID симметричного ключа в базе данных. Чтобы найти значение Key_ID, если известно только имя ключа, используйте функцию SYMKEY_ID. Аргумент *Key_ID* имеет тип данных **int**.  
  
 **'** algorithm_desc **'**  
 Указывает, что в выходных данных возвращается описание алгоритма симметричного ключа. Доступно только для симметричных ключей, созданных с помощью модуля расширенного управления ключами.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **sql_variant**  
  
## <a name="permissions"></a>Разрешения  
 Необходимы некоторые разрешения на симметричный ключ, а также для вызывающей стороны не должно быть запрещено разрешение VIEW на этот симметричный ключ.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается алгоритм симметричного ключа с идентификатором Key_ID 256.  
  
```  
SELECT SYMKEYPROPERTY(256, 'algorithm_desc') AS Algorithm ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [ASYMKEY_ID (Transact-SQL)](../../t-sql/functions/asymkey-id-transact-sql.md)   
 [ALTER SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [sys.symmetric_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [KEY_ID (Transact-SQL)](../../t-sql/functions/key-id-transact-sql.md)   
 [ASYMKEYPROPERTY (Transact-SQL)](../../t-sql/functions/asymkeyproperty-transact-sql.md)  
  
  
