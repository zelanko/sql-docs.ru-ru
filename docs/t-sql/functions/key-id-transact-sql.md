---
title: KEY_ID (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Key_ID
- Key_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- identification numbers [SQL Server], symmetric keys
- KEY_ID function
- symmetric keys [SQL Server], IDs
- IDs [SQL Server], symmetric keys
ms.assetid: d7309542-dbbe-41dc-b42e-5d9a1c8b4838
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1ffafacce7d82645d0f1e8c0335637d26d850798
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47604762"
---
# <a name="keyid-transact-sql"></a>KEY_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает идентификатор симметричного ключа текущей базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Key_ID ( 'Key_Name' )  
```  
  
## <a name="arguments"></a>Аргументы  
 **'** *Key_Name* **'**  
 Имя симметричного ключа в базе данных.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **int**  
  
## <a name="remarks"></a>Remarks  
 Имя временного ключа должно начинаться с символа (#).  
  
## <a name="permissions"></a>Разрешения  
 Так как временные ключи доступны только во время сеанса, в котором они были созданы, никаких разрешений для доступа к ним не требуется. Для получения доступа к ключу, который не является временным, у вызывающего должны быть разрешения на ключ и не должно быть запрещено разрешение VIEW для ключа.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-id-of-a-symmetric-key"></a>A. Возврат идентификатора симметричного ключа  
 Следующий пример возвращает идентификатор ключа `ABerglundKey1`.  
  
```  
SELECT KEY_ID('ABerglundKey1');  
```  
  
### <a name="b-returning-the-id-of-a-temporary-symmetric-key"></a>Б. Возврат идентификатора временного симметричного ключа  
 Следующий пример возвращает идентификатор временного симметричного ключа. Обратите внимание, что символ `#` добавляется в начало имени ключа.  
  
```  
SELECT KEY_ID('#ABerglundKey2');  
```  
  
## <a name="see-also"></a>См. также:  
 [KEY_GUID (Transact-SQL)](../../t-sql/functions/key-guid-transact-sql.md)   
 [CREATE SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [sys.symmetric_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [sys.key_encryptions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-key-encryptions-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
