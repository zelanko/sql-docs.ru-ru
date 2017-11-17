---
title: "ЗАПРЕТ разрешений на асимметричный ключ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [SQL Server], asymmetric keys
- encryption [SQL Server], asymmetric keys
- permissions [SQL Server], asymmetric keys
- asymmetric keys [SQL Server], permissions
- DENY statement, asymmetric keys
- cryptography [SQL Server], asymmetric keys
ms.assetid: dd7d8cd5-536b-460c-ab5b-cb4752bbdfaa
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 386db84b88813109e10d951689868a5c3931cff9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="deny-asymmetric-key-permissions-transact-sql"></a>DENY, запрет разрешений на асимметричный ключ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Запрещает разрешения для асимметричного ключа.  
   
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DENY { permission  [ ,...n ] }   
    ON ASYMMETRIC KEY :: asymmetric_key_name   
        TO database_principal [ ,...n ]  
    [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *разрешение*  
 Указывает разрешение, которое может быть запрещено для асимметричного ключа. Перечислены ниже.  
  
 НА АСИММЕТРИЧНЫЙ ключ **::***asymmetric_key_name*  
 Задает асимметричный ключ, для которого запрещается разрешение. Необходим квалификатор области «::».  
  
 *database_principal*  
 Задает участника, для которого запрещается разрешение, — Это может быть:  
  
-   пользователь базы данных;  
  
-   роль базы данных;  
  
-   роль приложения;  
  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
  
-   пользователь базы данных, сопоставленный с группой Windows;  
  
-   пользователь базы данных, сопоставленный с сертификатом;  
  
-   пользователь базы данных, сопоставленный асимметричному ключу;  
  
-   пользователь базы данных, не сопоставленный участнику [системы безопасности] на уровне сервера.  
  
 CASCADE  
 Указывает, что запрещаемое разрешение также запрещается для других участников, которым оно было предоставлено данным участником.  
  
 *denying_principal*  
 Задает участника, от которого участник, выполняющий данный запрос, получает право на запрет разрешения. Это может быть:  
  
-   пользователь базы данных;  
  
-   роль базы данных;  
  
-   роль приложения;  
  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
  
-   пользователь базы данных, сопоставленный с группой Windows;  
  
-   пользователь базы данных, сопоставленный с сертификатом;  
  
-   пользователь базы данных, сопоставленный асимметричному ключу;  
  
-   пользователь базы данных, не сопоставленный участнику [системы безопасности] на уровне сервера.  
  
## <a name="remarks"></a>Замечания  
 Асимметричный ключ — защищаемое на уровне базы данных содержимое базы данных, являющейся его родителем в иерархии разрешений. Ниже перечислены наиболее специфичные и ограниченные разрешения (вместе с наиболее общими разрешениями, куда они входят по импликации), которые могут быть предоставлены для ассиметричного ключа.  
  
|Разрешение асимметричного ключа|Содержится в разрешении асимметричного ключа|Содержится в разрешении базы данных|  
|-------------------------------|------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ASYMMETRIC KEY|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Требуется разрешение CONTROL на асимметричный ключ. При использовании предложения AS указанный участник должен являться владельцем асимметричного ключа.  
  
## <a name="see-also"></a>См. также:  
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

