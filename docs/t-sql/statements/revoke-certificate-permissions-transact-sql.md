---
title: REVOKE, отмена разрешений на сертификат (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], permissions
- permissions [SQL Server], certificates
- REVOKE statement, certificates
ms.assetid: 2272324a-98f2-42c6-88b1-96a99020c9e9
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 109ac82aab6881f5ab0a92305308654c0c6b5cfd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706958"
---
# <a name="revoke-certificate-permissions-transact-sql"></a>REVOKE, отмена разрешений на сертификат (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Отменяет разрешения на сертификат.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission  [ ,...n ]   
    ON CERTIFICATE :: certificate_name   
    { TO | FROM } database_principal [ ,...n ]  
    [ CASCADE ]  
    [ AS revoking_principal ]  
```  
  
## <a name="arguments"></a>Аргументы  
 GRANT OPTION FOR  
 Указывает, что возможность предоставлять указанное разрешение будет отменена. Само разрешение отменено не будет.  
  
> [!IMPORTANT]  
>  Если участник обладает указанным разрешением без параметра GRANT, будет отменено само разрешение.  
  
 *permission*  
 Обозначает разрешение, которое может быть отменено для сертификата. Перечислены ниже.  
  
 ON CERTIFICATE **::***certificate_name*  
 Указывает сертификат, для которого отменяется разрешение. Квалификатор области "::" является обязательным.  
  
 *database_principal*  
 Задает участника, у которого отменяется разрешение. Это может быть:  
  
-   пользователь базы данных;  
  
-   роль базы данных;  
  
-   роль приложения;  
  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
  
-   пользователь базы данных, сопоставленный с группой Windows;  
  
-   пользователь базы данных, сопоставленный с сертификатом;  
  
-   пользователь базы данных, сопоставленный с асимметричным ключом;  
  
-   пользователь базы данных, не сопоставленный с участником на уровне сервера.  
  
 CASCADE  
 Указывает, что отозванное разрешение отзывается также у других участников, которым оно было предоставлено этим участником.  
  
> [!CAUTION]  
>  Каскадная отмена разрешения, предоставленного с помощью параметра WITH GRANT OPTION, приведет к отмене разрешений GRANT и DENY для этого разрешения.  
  
 AS *revoking_principal*  
 Указывает участника, от которого участник, выполняющий данный запрос, получает право на отмену разрешения. Это может быть:  
  
-   пользователь базы данных;  
  
-   роль базы данных;  
  
-   роль приложения;  
  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
  
-   пользователь базы данных, сопоставленный с группой Windows;  
  
-   пользователь базы данных, сопоставленный с сертификатом;  
  
-   пользователь базы данных, сопоставленный с асимметричным ключом;  
  
-   пользователь базы данных, не сопоставленный с участником на уровне сервера.  
  
## <a name="remarks"></a>Примечания  
 Сертификат является защищаемым объектом уровня базы данных, содержащимся в базе данных, являющейся его родительским элементом в иерархии разрешений. Ниже перечислены наиболее специфичные и ограниченные разрешения (вместе с наиболее общими разрешениями, куда они входят неявно), которые могут быть отменены для сертификата.  
  
|Разрешение сертификата|Содержится в разрешении сертификата|Содержится в разрешении базы данных|  
|----------------------------|---------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY CERTIFICATE|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения CONTROL для сертификата.  
  
## <a name="see-also"></a>См. также:  
 [REVOKE (Transact-SQL)](../../t-sql/statements/revoke-transact-sql.md)   
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [CREATE APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/create-application-role-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
