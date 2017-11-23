---
title: "DENY, запрет разрешений на сборку (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- assemblies [CLR integration], permissions
- DENY statement, assemblies
- denying permissions [SQL Server], assemblies
ms.assetid: be0896b3-f793-44c9-9390-1c6e58f33b2b
caps.latest.revision: "31"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ed5de889401fb6c0c952541242dd1656e79875e8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="deny-assembly-permissions-transact-sql"></a>Запрещение (DENY) разрешений на сборки (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Запрещает разрешение на сборку.  
  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DENY { permission [ ,...n ] } ON ASSEMBLY :: assembly_name  
    TO database_principal [ ,...n ]   
        [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *разрешение*  
 Указывает разрешение на сборку, которое запрещается. Перечислены ниже.  
  
 В СБОРКЕ **::***assembly_name*  
 Указывает сборку, на которую запрещается разрешение. Необходим квалификатор области «::».  
  
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
 Сборка — это защищаемый объект уровня базы данных, который содержится в базе данных, являющейся его родителем в иерархии разрешений. Ряд основных разрешений на сборку, которые могут быть запрещены, перечислены ниже, вместе с более общими разрешениями, которые их подразумевают.  
  
|Разрешение сборки|Содержится в разрешении сборки|Содержится в разрешении базы данных|  
|-------------------------|------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ASSEMBLY|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение CONTROL на сборку. Если используется параметр AS, указанный участник должен быть владельцем сборки.  
  
## <a name="see-also"></a>См. также:  
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [СОЗДАТЬ РОЛЬ приложения &#40; Transact-SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [СОЗДАТЬ СБОРКУ &#40; Transact-SQL &#41;](../../t-sql/statements/create-assembly-transact-sql.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
