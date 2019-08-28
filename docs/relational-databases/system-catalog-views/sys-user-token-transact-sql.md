---
title: sys. user_token (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/27/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.user_token
- user_token
- sys.user_token_TSQL
- user_token_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- logins [SQL Server], security tokens
- sys.user_token catalog view
- user tokens [SQL Server]
- tokens [SQL Server]
- user_token catalog view
ms.assetid: be018103-5e57-43a4-9160-9bf420892aa7
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9e2f093083277d23bad91ea268da0026d6c4dc1a
ms.sourcegitcommit: f517f1e2e7cac983fdb41229e60ca7ad019ecd48
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2019
ms.locfileid: "70064039"
---
# <a name="sysuser_token-transact-sql"></a>sys.user_token (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md.md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Возвращает по одной строке на каждого участника базы данных, который входит в токен пользователя в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**principal_id**|**int**|Идентификатор участника. Значение уникально в пределах базы данных.|  
|**трансляцию**|**varbinary(85)**|Идентификатор защиты участника, если он определен как внешний по отношению к базе данных. Например: это может быть имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], имя входа Windows, группа Windows или имя входа, сопоставленное с сертификатом. В противном случае этот столбец содержит значение NULL.|  
|**name**|**nvarchar (128)**|Имя участника. Значение уникально в пределах базы данных.|  
|**type**|**nvarchar (128)**|Описание типа участника. Все типы сопоставлены с **SID**. Значение может быть одним из следующих:<br /><br /> SQL USER;<br /><br /> WINDOWS LOGIN<br /><br /> WINDOWS GROUP<br /><br /> ROLE<br /><br /> APPLICATION ROLE<br /><br /> DATABASE ROLE<br /><br /> USER MAPPED TO CERTIFICATE;<br /><br /> USER MAPPED TO ASYMMETRIC KEY;<br /><br /> CERTIFICATE<br /><br /> ASYMMETRIC KEY|  
|**Загрузка**|**nvarchar (128)**|Указывает, что участник задействован в процессе определения разрешений GRANT и DENY или выполняет роль средства проверки подлинности.<br /><br /> Значение может быть одним из следующих.<br /><br /> GRANT OR DENY;<br /><br /> DENY ONLY;<br /><br /> AUTHENTICATOR.|  
  
## <a name="see-also"></a>См. также  
 [sys. login_token &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-login-token-transact-sql.md)   
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
