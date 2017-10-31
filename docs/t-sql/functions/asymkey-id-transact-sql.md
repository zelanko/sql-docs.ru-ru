---
title: "ASYMKEY_ID (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AsymKey_ID
- ASYMKEY_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- asymmetric keys [SQL Server], AsymKey_ID
- ASYMKEY_ID function
- encryption [SQL Server], asymmetric keys
- identification numbers [SQL Server], asymmetric keys
- IDs [SQL Server], asymmetric keys
- cryptography [SQL Server], asymmetric keys
ms.assetid: d697daf8-2106-4ebb-b09a-ca0be465d747
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 765e97c83af76616f706018481e626ecb07bcc53
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="asymkeyid-transact-sql"></a>ASYMKEY_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает идентификатор асимметричного ключа.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
ASYMKEY_ID ( 'Asym_Key_Name' )  
```  
  
## <a name="arguments"></a>Аргументы  
*Asym_Key_Name*  
Имя асимметричного ключа в базе данных.
  
## <a name="return-types"></a>Возвращаемые типы
 **int**  
  
## <a name="permissions"></a>Permissions  
Требует некоторых разрешений асимметричного ключа, а также подтверждения разрешения вызывающей стороны на VIEW с этим асимметричным ключом.
  
## <a name="examples"></a>Примеры  
Следующий пример возвращает идентификатор асимметричного ключа `ABerglundKey11`.
  
```sql
SELECT ASYMKEY_ID('ABerglundKey11');  
GO  
```  
  
## <a name="see-also"></a>См. также:
[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)  
[ALTER ASYMMETRIC KEY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)  
[DROP ASYMMETRIC KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)  
[SIGNBYASYMKEY (Transact-SQL)](../../t-sql/functions/signbyasymkey-transact-sql.md)  
[VERIFYSIGNEDBYASYMKEY &#40; Transact-SQL &#41;](../../t-sql/functions/verifysignedbyasymkey-transact-sql.md)  
[Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
[sys.asymmetric_keys &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-asymmetric-keys-transact-sql.md)  
[Представления каталога безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)  
[ASYMKEYPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/asymkeyproperty-transact-sql.md)  
[KEY_ID &#40; Transact-SQL &#41;](../../t-sql/functions/key-id-transact-sql.md)
  
  

