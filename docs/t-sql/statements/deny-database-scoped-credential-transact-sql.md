---
title: "ЗАПРЕТИТЬ учетных данных (Transact-SQL) в области базы данных | Документы Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DENY DATABASE SCOPED CREDENTIAL
- DENY_DATABASE_SCOPED_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DENY statement, database scoped credentials
- denying permissions [SQL Server], database scoped credential
ms.assetid: c508b1c9-169e-4e7a-9a49-7ddf2ca8f848
caps.latest.revision: 2
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dcb2ee7f32cea0c848850dc504a91067611b743e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="deny-database-scoped-credential-transact-sql"></a>ЗАПРЕЩАЮЩИЕ области базы данных учетных данных (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Запрещает разрешения на учетные данные уровня базы данных.  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DENY permission  [ ,...n ]   
    ON DATABASE SCOPED CREDENTIAL :: credential_name   
    TO principal [ ,...n ]  
    [ CASCADE ]  
    [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *разрешение*  
 Указывает разрешение, которое может быть запрещено на учетные данные уровня базы данных. Перечислены ниже.  
  
 В учетных данных области базы данных **::***credential_name*  
 Задает учетные данные уровня базы данных, для которого запрещается разрешение. Необходим квалификатор области «::».  
  
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
 Учетные данные уровня базы данных — это защищаемый объект уровня базы данных, содержащихся в базе данных, которая является родительской в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые могут быть запрещены на учетные данные уровня базы данных перечислены ниже вместе с более общими разрешениями, неявно их содержащими.  
  
|Разрешение учетных данных области базы данных|Содержится в разрешении учетные данные уровня базы данных|Содержится в разрешении базы данных|  
|----------------------------|---------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение CONTROL на учетные данные уровня базы данных. При использовании предложения AS указанный участник должен быть владельцем учетные данные уровня базы данных.  
  
## <a name="see-also"></a>См. также:  
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
 [В области базы данных GRANT учетных данных (Transact-SQL)](../../t-sql/statements/grant-database-scoped-credential-transact-sql.md)   
 [ОТОЗВАТЬ учетные данные уровня базы данных (Transact-SQL)](../../t-sql/statements/revoke-database-scoped-credential-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

