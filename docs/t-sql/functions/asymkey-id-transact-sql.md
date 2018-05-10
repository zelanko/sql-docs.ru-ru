---
title: ASYMKEY_ID (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
manager: craigg
ms.openlocfilehash: 0fe892af66714c2ab9995dab6c5435ee52908c12
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="asymkeyid-transact-sql"></a>ASYMKEY_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает идентификатор асимметричного ключа.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
ASYMKEY_ID ( 'Asym_Key_Name' )  
```  
  
## <a name="arguments"></a>Аргументы  
*Asym_Key_Name*  
Имя асимметричного ключа в базе данных.
  
## <a name="return-types"></a>Типы возвращаемых данных
 **int**  
  
## <a name="permissions"></a>Разрешения  
Необходимы подходящие разрешения на асимметричный ключ, а также для вызывающей стороны не должно быть запрещено разрешение VIEW на этот асимметричный ключ. Дополнительные сведения о разрешениях для асимметричных ключей см. в разделе [CREATE ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/create-asymmetric-key-transact-sql.md).
  
## <a name="examples"></a>Примеры  
Этот пример возвращает идентификатор асимметричного ключа `ABerglundKey11`.
  
```sql
SELECT ASYMKEY_ID('ABerglundKey11');  
GO  
```  
  
## <a name="see-also"></a>См. также раздел
[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)  
[ALTER ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)  
[DROP ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)  
[SIGNBYASYMKEY (Transact-SQL)](../../t-sql/functions/signbyasymkey-transact-sql.md)  
[VERIFYSIGNEDBYASYMKEY (Transact-SQL)](../../t-sql/functions/verifysignedbyasymkey-transact-sql.md)  
[Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
[sys.asymmetric_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-asymmetric-keys-transact-sql.md)  
[Представления каталога безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)  
[ASYMKEYPROPERTY (Transact-SQL)](../../t-sql/functions/asymkeyproperty-transact-sql.md)  
[KEY_ID (Transact-SQL)](../../t-sql/functions/key-id-transact-sql.md)
  
  
