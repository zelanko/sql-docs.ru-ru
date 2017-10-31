---
title: "Запрет разрешения на симметричный ключ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [SQL Server], symmetric keys
- symmetric keys [SQL Server], permissions
- permissions [SQL Server], symmetric keys
- DENY statement, symmetric keys
- encryption [SQL Server], symmetric keys
- cryptography [SQL Server], symmetric keys
ms.assetid: 52d4b12d-17be-4cbd-aa78-65332a4883b0
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d6497a6bcf298736b3ad6c497ea26088e9fdf0a1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="deny-symmetric-key-permissions-transact-sql"></a>DENY, запрет разрешений на симметричный ключ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Запрещает разрешения для симметричного ключа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DENY permission [ ,...n ]    
    ON SYMMETRIC KEY :: symmetric_key_name   
        TO <database_principal> [ ,...n ] [ CASCADE ]  
    [ AS <database_principal> ]   
  
<database_principal> ::=   
        Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login   
```  
  
## <a name="arguments"></a>Аргументы  
 *разрешение*  
 Обозначает разрешение, которое можно запретить для симметричного ключа. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 СИММЕТРИЧНЫЙ ключ ON::*asymmetric_key_name*  
 Указывает симметричный ключ, для которого снимается разрешение. Требуется квалификатор области (::).  
  
 Чтобы \< *database_principal*>  
 Задает участника, у которого отменяется разрешение.  
  
 CASCADE  
 Указывает, что запрещаемое разрешение также запрещается для других участников, которым оно было предоставлено данным участником.  
  
 AS \<database_principal >  
 Задает участника, от которого участник, выполняющий данный запрос, получает право на запрет разрешения.  
  
 *Пользователь_базы_данных*  
 Указывает пользователя базы данных.  
  
 *Database_role*  
 Указывает роль базы данных.  
  
 *Application_role*  
 Указывает роль приложения.  
  
 *Database_user_mapped_to_Windows_User*  
 Указывает пользователя базы данных, сопоставленного с пользователем Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
 Указывает пользователя базы данных, сопоставленного с группой Windows.  
  
 *Database_user_mapped_to_certificate*  
 Указывает пользователя базы данных, сопоставленного с сертификатом.  
  
 *Database_user_mapped_to_asymmetric_key*  
 Указывает пользователя базы данных, сопоставленного с асимметричным ключом.  
  
 *Database_user_with_no_login*  
 Указывает пользователя базы данных, не сопоставленного с субъектом серверного уровня.  
  
## <a name="remarks"></a>Замечания  
 Сведения о симметричных ключах можно увидеть в [sys.symmetric_keys](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md) представления каталога.  
  
 Симметричный ключ — это такой защищаемый объект уровня базы данных, который находится в базе данных, являющейся его родителем в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно снять для симметричного ключа, перечислены в следующей таблице вместе с более общими разрешениями, неявно содержащими их.  
  
|Разрешение на симметричный ключ|Содержится в разрешении симметричного ключа|Содержится в разрешении базы данных|  
|------------------------------|-----------------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY SYMMETRIC KEY|  
|CONTROL|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение CONTROL для симметричного ключа или разрешение ALTER ANY SYMMETRIC KEY для базы данных. При использовании параметра AS указанный участник должен являться владельцем симметричного ключа.  
  
## <a name="examples"></a>Примеры  
 В следующем примере снимается разрешение `ALTER` для симметричного ключа `SamInventory42` для пользователя базы данных `HamidS`.  
  
```  
USE AdventureWorks2012;  
DENY ALTER ON SYMMETRIC KEY::SamInventory42 TO HamidS;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.symmetric_keys &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [ПРЕДОСТАВЬТЕ разрешения на симметричный ключ &#40; Transact-SQL &#41;](../../t-sql/statements/grant-symmetric-key-permissions-transact-sql.md)   
 [ОТОЗВАТЬ разрешения на симметричный ключ &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-symmetric-key-permissions-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

