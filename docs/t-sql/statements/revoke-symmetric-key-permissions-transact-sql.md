---
title: REVOKE, отмена разрешения на симметричный ключ (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], permissions
- permissions [SQL Server], symmetric keys
- REVOKE statement, symmetric keys
ms.assetid: 091da030-a768-4aa3-9509-cc23bd719cea
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 33c1a7821f532249c13400c3937706267e22bf7d
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "67914184"
---
# <a name="revoke-symmetric-key-permissions-transact-sql"></a>REVOKE, отмена разрешения на симметричный ключ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Отменяет предоставленные и запрещенные разрешения на симметричный ключ.  
   
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ]    
    ON SYMMETRIC KEY :: symmetric_key_name   
        { TO | FROM } <database_principal> [ ,...n ]   
    [ CASCADE ]  
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
 *permission*  
 Задает разрешение на симметричный ключ, которое может быть отменено. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
 ON SYMMETRIC KEY :: *asymmetric_key_name*  
 Задает симметричный ключ, для которого отменяется разрешение. Квалификатор области (::) является обязательным.  
  
 GRANT OPTION  
 Показывает, что отменяется право на предоставление указанного разрешения другим участникам. Само разрешение отменено не будет.  
  
> [!IMPORTANT]  
>  Если участник обладает указанным разрешением без параметра GRANT, будет отменено само разрешение.  
  
 CASCADE  
 Показывает, что отменяемое разрешение также отменяется для других участников, для которых оно было предоставлено или запрещено данным участником.  
  
> [!CAUTION]  
>  Каскадная отмена разрешения, предоставленного с помощью параметра WITH GRANT OPTION, приведет к отмене разрешений GRANT и DENY для этого разрешения.  
  
 { TO | FROM } \<*database_principal*>  
 Задает участника, у которого отменяется разрешение.  
  
 AS \<database_principal> Указывает субъекта, от которого субъект, выполняющий данный запрос, наследует право на отмену разрешения.  
  
 *Database_user*  
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
  
## <a name="remarks"></a>Remarks  
 Сведения о симметричных ключах доступны в представлении каталога [sys.symmetric_keys](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md).  
  
 Если при отмене разрешения у участника, получившего его с помощью параметра GRANT OPTION, не был задан параметр CASCADE, выполнение инструкции завершается с ошибкой.  
  
 Симметричный ключ — это такой защищаемый объект уровня базы данных, который находится в базе данных, являющейся его родителем в иерархии разрешений. Наиболее специальные и ограниченные разрешения, которые могут быть предоставлены на симметричном ключе, перечислены в следующей таблице вместе с более общими разрешениями, содержащими их по включению.  
  
|Разрешение симметричного ключа|Содержится в разрешении симметричного ключа|Содержится в разрешении базы данных|  
|------------------------------|-----------------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY SYMMETRIC KEY|  
|CONTROL|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL для симметричного ключа или разрешение ALTER ANY SYMMETRIC KEY для базы данных. При использовании параметра AS указанный участник должен являться владельцем симметричного ключа.  
  
## <a name="examples"></a>Примеры  
 В ходе выполнения следующего примера производится отмена разрешения `ALTER` по симметричному ключу `SamInventory42` для пользователя `HamidS`, а также для других участников, получивших от `HamidS` разрешение `ALTER`.  
  
```  
USE AdventureWorks2012;  
REVOKE ALTER ON SYMMETRIC KEY::SamInventory42 TO HamidS CASCADE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.symmetric_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [Разрешения GRANT на симметричный ключ (Transact-SQL)](../../t-sql/statements/grant-symmetric-key-permissions-transact-sql.md)   
 [DENY, запрет разрешений на симметричный ключ (Transact-SQL)](../../t-sql/statements/deny-symmetric-key-permissions-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

