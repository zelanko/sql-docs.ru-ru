---
title: "GRANT, предоставление разрешений для сборки (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 06/12/2017
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
- granting permissions [SQL Server], assemblies
- assemblies [CLR integration], permissions
- GRANT statement, assemblies
ms.assetid: dce1e027-f859-4967-bdda-16a95ae460d0
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d163245f90ce50defdea4b7a075ef9d0fb9b5afd
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="grant-assembly-permissions-transact-sql"></a>Разрешения для сборки GRANT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Предоставляет разрешения для сборки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
GRANT { permission [ ,...n ] } ON ASSEMBLY :: assembly_name  
    TO database_principal [ ,...n ]  
    [ WITH GRANT OPTION ]  
    [ AS granting_principal ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *permission*  
 Указывает разрешение, которое может быть предоставлено для сборки. Перечислены ниже.  
  
 ON ASSEMBLY **::***assembly_name*  
 Указывает сборку, для которой предоставляется разрешение. Необходим квалификатор области «::».  
  
 *database_principal*  
 Участник, которому предоставляется разрешение. Это может быть:  
  
-   пользователь базы данных;  
-   роль базы данных;  
-   роль приложения;  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
-   пользователь базы данных, сопоставленный с группой Windows;  
-   пользователь базы данных, сопоставленный с сертификатом;  
-   пользователь базы данных, сопоставленный асимметричному ключу;  
-   пользователь базы данных, не сопоставленный участнику [системы безопасности] на уровне сервера.  
  
GRANT OPTION  
 Показывает, что участнику будет дана возможность предоставлять указанное разрешение другим участникам.  
  
AS *granting_principal*  
 Указывает участника, от которого участник, выполняющий данный запрос, наследует право на предоставление разрешения. Это может быть:  
  
-   пользователь базы данных;  
-   роль базы данных;  
-   роль приложения;  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
-   пользователь базы данных, сопоставленный с группой Windows;  
-   пользователь базы данных, сопоставленный с сертификатом;  
-   пользователь базы данных, сопоставленный асимметричному ключу;  
-   пользователь базы данных, не сопоставленный участнику [системы безопасности] на уровне сервера.  
  
## <a name="remarks"></a>Remarks  
 Сборка — это защищаемый объект уровня базы данных, который содержится в базе данных, являющейся его родителем в иерархии разрешений. Ниже перечислены наиболее специфичные и ограниченные разрешения (вместе с более общими разрешениями, куда они входят по импликации), которые могут быть выданы для сборки.  
  
|Разрешение сборки|Содержится в разрешении сборки|Содержится в разрешении базы данных|  
|-------------------------|------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ASSEMBLY|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
 Объект, предоставляющий разрешение (или участник, указанный параметром AS), должен иметь либо само разрешение, выданное с помощью параметра GRANT OPTION, либо разрешение более высокого уровня, которое неявно включает предоставляемое.  
  
 Если используется параметр AS, налагаются следующие дополнительные требования.  
  
|AS *granting_principal*|Необходимо дополнительное разрешение|  
|------------------------------|------------------------------------|  
|Пользователь базы данных|Разрешение IMPERSONATE для пользователя, членство в предопределенной роли базы данных **db_securityadmin**, членство в предопределенной роли базы данных **db_owner** или членство в предопределенной роли сервера **sysadmin**.|  
|Пользователь базы данных, сопоставленный имени входа Windows|Разрешение IMPERSONATE для пользователя, членство в предопределенной роли базы данных **db_securityadmin**, членство в предопределенной роли базы данных **db_owner** или членство в предопределенной роли сервера **sysadmin**.|  
|Пользователь базы данных, сопоставленный группе Windows|Членство в группе Windows, членство в предопределенной роли базы данных **db_securityadmin**, членство в предопределенной роли базы данных **db_owner** или членство в предопределенной роли сервера **sysadmin**.|  
|Пользователь базы данных, сопоставленный сертификату|Членство в предопределенной роли базы данных **db_securityadmin**, членство в предопределенной роли базы данных **db_owner** или членство в предопределенной роли сервера **sysadmin**.|  
|Пользователь базы данных, сопоставленный асимметричному ключу|Членство в предопределенной роли базы данных **db_securityadmin**, членство в предопределенной роли базы данных **db_owner** или членство в предопределенной роли сервера **sysadmin**.|  
|Пользователь базы данных, не сопоставленный ни с одним участником на уровне сервера|Разрешение IMPERSONATE для пользователя, членство в предопределенной роли базы данных **db_securityadmin**, членство в предопределенной роли базы данных **db_owner** или членство в предопределенной роли сервера **sysadmin**.|  
|Роль базы данных|Разрешение ALTER на роль, членство в предопределенной роли базы данных **db_securityadmin**, предопределенной роли базы данных **db_owner** или предопределенной роли сервера **sysadmin**.|  
|Роль приложения|Разрешение ALTER на роль, членство в предопределенной роли базы данных **db_securityadmin**, предопределенной роли базы данных **db_owner** или предопределенной роли сервера **sysadmin**.|  
  
 Владельцы объектов могут предоставлять разрешения на объекты, которыми они владеют. Участники, имеющие разрешение CONTROL на защищаемый объект, могут предоставлять разрешение на этот защищаемый объект.  
  
 Участники, которым предоставлено разрешение CONTROL SERVER, такие как члены предопределенной роли сервера **sysadmin**, могут предоставлять любое разрешение для любого защищаемого объекта сервера. Участники, получившие разрешение CONTROL для базы данных, такие как члены предопределенной роли базы данных **db_owner**, могут предоставлять любое разрешение для любого защищаемого объекта в базе данных. Владельцы разрешения CONTROL, связанного со схемой, могут предоставлять любые разрешения на работу с любыми объектами, содержащимися в данной схеме.  
  
## <a name="see-also"></a>См. также:  
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [CREATE APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/create-application-role-transact-sql.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
