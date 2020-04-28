---
title: sys. master_key_passwords (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/06/2020
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
ms.openlocfilehash: 926acd9beb00102e19dbc2844e282d74bc890915
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "80752896"
---
# <a name="sysmaster_key_passwords-transact-sql"></a>sys.master_key_passwords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Возвращает строку для каждого пароля главного ключа базы данных, добавленного с помощью хранимой процедуры **sp_control_dbmasterkey_password** . Пароли, используемые для защиты главного ключа, хранятся в хранилище учетных данных. Имя учетных данных имеет следующий формат: # #DBMKEY_<database_family_guid>_<random_password_guid> # #. Пароль хранится как секретные учетные данные. Для каждого пароля, добавленного с помощью **sp_control_dbmasterkey_password**, существует строка в **представлении sys. Credentials**.  
  
 Каждая строка в этом представлении показывает **credential_id** и **family_guid** базы данных главный ключ, защищенный паролем, связанным с этими учетными данными. Соединение с **sys. Credentials** на **credential_id** возвратит полезные поля, такие как **create_date** и имя учетных данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**credential_id**|**int**|Идентификатор учетных данных, которым принадлежит данный пароль. Этот идентификатор уникален в экземпляре сервера.|  
|**family_guid**|**uniqueidentifier**|Уникальный идентификатор оригинальной базы данных в момент создания. Этот идентификатор GUID остается неизменным после восстановления или присоединения базы данных, даже если имя базы данных изменилось.<br /><br /> В случае сбоя автоматической расшифровки главного ключа службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует **family_guid** для указания учетных данных, которые могут содержать пароль, используемый для защиты главного ключа базы данных.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [Представления каталога безопасности &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Создание &#40;ов на основе СИММЕТРИЧНого ключа&#41;Transact-SQL](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
