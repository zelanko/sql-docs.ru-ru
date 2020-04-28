---
title: sys. sql_logins (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/20/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sql_logins_TSQL
- sql_logins_TSQL
- sys.sql_logins
- sql_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_logins catalog view
ms.assetid: 0d9c5b09-86fe-40ff-baab-00b7c051402f
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c3dba46f4d0e2ecdebda13fe3fe9412219c2a755
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "79448474"
---
# <a name="syssql_logins-transact-sql"></a>sys.sql_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  Возвращает по одной строке для каждой учетной записи проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<наследуемые столбцы>**|--|Наследуется от **sys. server_principals**.|  
|**is_policy_checked**|**bit**|Проверяется политика паролей.|  
|**is_expiration_checked**|**bit**|Проверяется истечение срока действия паролей.|  
|**password_hash**|**varbinary (256)**|Хэш пароля имени входа SQL. Начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] сохраненные сведения о пароле вычисляются с помощью SHA-512 соленого пароля.|  
  
 Список столбцов, наследуемых этим представлением, см. в разделе [sys. server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md). Столбцы `owning_principal_id` и `is_fixed_role` не наследуются из sys. server_principals.
  
## <a name="remarks"></a>Remarks  
 Чтобы просмотреть имена [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа для проверки подлинности и имена входа для проверки подлинности Windows, см. раздел [sys. Server_principals &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
 Если пользователи автономной базы данных включены, то подключения могут выполняться без имен входа. Чтобы определить эти учетные записи, см. раздел [sys. database_principals &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Любое имя входа проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может видеть собственное имя входа и имя входа sa. Для просмотра других имен входа требуется разрешение ALTER ANY LOGIN или разрешение на имя входа.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога безопасности &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Политика паролей](../../relational-databases/security/password-policy.md)   
 [Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
