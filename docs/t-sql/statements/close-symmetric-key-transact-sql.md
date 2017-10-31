---
title: "CLOSE SYMMETRIC KEY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CLOSE SYMMETRIC KEY
- CLOSE_SYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- closing symmetric keys
- encryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], closing
- CLOSE SYMMETRIC KEY statement
- cryptography [SQL Server], symmetric keys
ms.assetid: 3b083cbb-3c6a-4f59-8d34-601db1efcc83
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 18a4215cf009ebf89bf6ce709c0517455731c4b5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="close-symmetric-key-transact-sql"></a>CLOSE SYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Закрывает симметричный ключ или все симметричные ключи, открытые в текущем сеансе.  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CLOSE { SYMMETRIC KEY key_name | ALL SYMMETRIC KEYS }  
```  
  
## <a name="arguments"></a>Аргументы  
 *Key_name*  
 Имя симметричного ключа, который следует закрыть.  
  
## <a name="remarks"></a>Замечания  
 Открытые симметричные ключи привязаны к сеансу, а не к контексту безопасности. Открытый ключ останется доступным, пока не будет явно закрыт или сеанс не будет прерван. ЗАКРЫТЬ все SYMMETRIC KEYS закрывает любой главный ключ базы данных, который был открыт в текущем сеансе с помощью [OPEN MASTER KEY](../../t-sql/statements/open-master-key-transact-sql.md) инструкции.  Сведения об открытых ключах можно увидеть в [sys.openkeys &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-openkeys-transact-sql.md) представления каталога.  
  
## <a name="permissions"></a>Permissions  
 Явного разрешения на закрытие симметричного ключа не требуется.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-closing-a-symmetric-key"></a>A. Закрытие симметричного ключа  
 Следующий код закрывает симметричный ключ `ShippingSymKey04`.  
  
```  
CLOSE SYMMETRIC KEY ShippingSymKey04;  
GO  
```  
  
### <a name="b-closing-all-symmetric-keys"></a>Б. Закрытие всех симметричных ключей  
 Следующий код закрывает все симметричные ключи, открытые в текущем сеансе, а также явно открытый главный ключ базы данных.  
  
```  
CLOSE ALL SYMMETRIC KEYS;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [OPEN SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [УДАЛЯТЬ СИММЕТРИЧНЫЙ ключ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)  
  
  

