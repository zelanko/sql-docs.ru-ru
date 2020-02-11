---
title: sys. master_key_passwords (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 87bb4a97db318330f253d068febb1309e4eda12a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68102406"
---
# <a name="sysmaster_key_passwords-transact-sql"></a>sys.master_key_passwords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строку для каждого пароля главного ключа базы данных, добавленного с помощью хранимой процедуры **sp_control_dbmasterkey_password** . Пароли, используемые для защиты главного ключа, хранятся в хранилище учетных данных. Имя учетных данных имеет следующий формат: # #DBMKEY_<database_family_guid>_<random_password_guid> # #. Пароль хранится как секретные учетные данные. Для каждого пароля, добавленного с помощью **sp_control_dbmasterkey_password**, существует строка в **представлении sys. Credentials**.  
  
 Каждая строка в этом представлении показывает **credential_id** и **family_guid** базы данных главный ключ, защищенный паролем, связанным с этими учетными данными. Соединение с **sys. Credentials** на **credential_id** возвратит полезные поля, такие как **create_date** и имя учетных данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**credential_id**|**int**|Идентификатор учетных данных, которым принадлежит данный пароль. Этот идентификатор уникален в экземпляре сервера.|  
|**family_guid**|**UNIQUEIDENTIFIER**|Уникальный идентификатор оригинальной базы данных в момент создания. Этот идентификатор GUID остается неизменным после восстановления или присоединения базы данных, даже если имя базы данных изменилось.<br /><br /> В случае сбоя автоматической расшифровки главного ключа службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует **family_guid** для указания учетных данных, которые могут содержать пароль, используемый для защиты главного ключа базы данных.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Дополнительные сведения см. в разделе [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [Представления каталога безопасности &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
