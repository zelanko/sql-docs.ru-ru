---
title: sys.master_key_passwords (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.master_key_passwords_TSQL
- master_key_passwords_TSQL
- sys.master_key_passwords
- master_key_passwords
dev_langs:
- TSQL
helpviewer_keywords:
- sys.master_key_passwords catalog view
ms.assetid: b8e18cff-a9e6-4386-98ce-1cd855506e03
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ea8e225af776493f2a191ea83ce591c51ba624c8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysmasterkeypasswords-transact-sql"></a>sys.master_key_passwords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждого пароля главного ключа базы данных, добавленные с помощью **sp_control_dbmasterkey_password** хранимой процедуры. Пароли, используемые для защиты главного ключа, хранятся в хранилище учетных данных. Имя учетных данных имеет следующий формат: ## DBMKEY_ < database_family_guid > _ < random_password_guid > ##. Пароль хранится как секретные учетные данные. Для каждого пароля, добавленного с помощью **sp_control_dbmasterkey_password**, строка в **sys.credentials**.  
  
 Каждая строка в этом представлении содержит **credential_id** и **family_guid** главный ключ которой защищен паролем, связанные с этими учетными данными базы данных. Соединения с **sys.credentials** на **credential_id** возвратит полезные поля, такие как **create_date** и имя учетных данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**credential_id**|**int**|Идентификатор учетных данных, которым принадлежит данный пароль. Этот идентификатор уникален в экземпляре сервера.|  
|**family_guid**|**uniqueidentifier**|Уникальный идентификатор оригинальной базы данных в момент создания. Этот идентификатор GUID остается неизменным после восстановления или присоединения базы данных, даже если имя базы данных изменилось.<br /><br /> Если автоматическая расшифровка главного ключа службы завершается ошибкой, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует **family_guid** для идентификации учетных данных, которые могут содержать пароль, используемый для защиты главного ключа базы данных.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_control_dbmasterkey_password (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [CREATE SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
