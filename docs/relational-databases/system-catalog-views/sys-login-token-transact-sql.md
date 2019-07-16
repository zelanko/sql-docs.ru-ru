---
title: sys.login_token (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- login_token_TSQL
- sys.login_token_TSQL
- sys.login_token
- login_token
dev_langs:
- TSQL
helpviewer_keywords:
- sys.login_token catalog view
- logins [SQL Server], security tokens
- tokens [SQL Server]
ms.assetid: 86e06938-9d0a-44e5-99e2-55c8ef5f2f84
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: fb396d47da69724d16c0d72e1373527f9c5e700f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68102430"
---
# <a name="syslogintoken-transact-sql"></a>sys.login_token (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждого участника сервера, являющегося частью токена имени входа.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**principal_id**|**int**|Идентификатор участника. Это значение уникально в пределах сервера.|  
|**ИД безопасности**|**varbinary(85)**|Идентификатор безопасности участника. Если это участник Windows, **sid** = идентификатор безопасности Windows. Если имя входа сопоставлено с сертификатом, **sid** равно идентификатору GUID из сертификата.|  
|**name**|**nvarchar(128)**|Имя участника. Это значение уникально в пределах сервера.|  
|**type**|**nvarchar(128)**|Описание типа участника. Все типы сопоставляются с **sid**. Значение может быть одним из следующих:<br /><br /> SQL LOGIN<br /><br /> WINDOWS LOGIN<br /><br /> WINDOWS GROUP<br /><br /> SERVER ROLE<br /><br /> LOGIN MAPPED TO CERTIFICATE<br /><br /> LOGIN MAPPED TO ASYMMETRIC KEY<br /><br /> CERTIFICATE<br /><br /> ASYMMETRIC KEY|  
|**Использование**|**nvarchar(128)**|Указывает, что участник задействован в процессе определения разрешений GRANT и DENY или выполняет роль средства проверки подлинности.<br /><br /> Значение может быть одним из следующих.<br /><br /> GRANT OR DENY;<br /><br /> DENY ONLY;<br /><br /> AUTHENTICATOR.|  
  
## <a name="see-also"></a>См. также  
 [sys.user_token &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-user-token-transact-sql.md)   
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
