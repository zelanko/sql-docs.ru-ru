---
title: "sys.sql_logins (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/20/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sql_logins_TSQL
- sql_logins_TSQL
- sys.sql_logins
- sql_logins
dev_langs: TSQL
helpviewer_keywords: sys.sql_logins catalog view
ms.assetid: 0d9c5b09-86fe-40ff-baab-00b7c051402f
caps.latest.revision: "43"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 12dcc799255ebc44ed2b8d6401de80a98d83bcbb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="syssqllogins-transact-sql"></a>sys.sql_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  Возвращает по одной строке для каждой учетной записи проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**\<унаследованные столбцы >**|--|Наследует от **sys.server_principals**.|  
|**is_policy_checked**|**bit**|Проверяется политика паролей.|  
|**is_expiration_checked**|**bit**|Проверяется истечение срока действия паролей.|  
|**password_hash**|**varbinary(256)**|Хэш пароля имени входа SQL. Начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]сохраненные сведения о пароле вычисляется с помощью SHA-512 криптографического пароля.|  
  
 Список столбцов, наследуемых этим представлением см. в разделе [sys.server_principals &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
## <a name="remarks"></a>Замечания  
 Чтобы просмотреть оба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетные данные для входа и имена входа проверки подлинности Windows, в разделе [sys.server_principals &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
 Когда Автономные пользователи базы данных включены, подключения могут выполняться без имен входа. Для идентификации этих учетных записей, в разделе [sys.database_principals &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Любое имя входа проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может видеть собственное имя входа и имя входа sa. Для просмотра других имен входа требуется разрешение ALTER ANY LOGIN или разрешение на имя входа.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Политика паролей](../../relational-databases/security/password-policy.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
