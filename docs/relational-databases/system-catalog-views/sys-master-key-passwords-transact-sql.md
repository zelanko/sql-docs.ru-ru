---
title: sys.master_key_passwords (Трансакт-СЗЛ) Документы Майкрософт
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
ms.sourcegitcommit: c6a2efe551e37883c1749bdd9e3c06eb54ccedc9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80752896"
---
# <a name="sysmaster_key_passwords-transact-sql"></a>sys.master_key_passwords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Возвращает строку для каждого ключа главного ключа базы данных, добавленного с помощью процедуры **sp_control_dbmasterkey_password** сохранены. Пароли, используемые для защиты главного ключа, хранятся в хранилище учетных данных. Имя учетных данных следует этому формату: «#DBMKEY_<database_family_guid<>_>_<random_password_guid>». Пароль хранится как секретные учетные данные. Для каждого пароля, добавленного с помощью **sp_control_dbmasterkey_password,** есть строка в **sys.credentials.**  
  
 Каждая строка в этом представлении показывает **credential_id** и **family_guid** базы данных, главный ключ которой защищен паролем, связанным с этим учетным данным. Соединение с **sys.credentials** на **credential_id** вернет полезные поля, такие как **create_date** и имя учетных данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**credential_id**|**Int**|Идентификатор учетных данных, которым принадлежит данный пароль. Этот идентификатор уникален в экземпляре сервера.|  
|**family_guid**|**Uniqueidentifier**|Уникальный идентификатор оригинальной базы данных в момент создания. Этот идентификатор GUID остается неизменным после восстановления или присоединения базы данных, даже если имя базы данных изменилось.<br /><br /> Если автоматическая расшифровка ключом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастера службы не удается, использует **family_guid** для идентификации учетных данных, которые могут содержать пароль, используемый для защиты главного ключа базы данных.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Просмотры каталогов &#40;&#41;«Трансакт-СЗЛ»](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_control_dbmasterkey_password &#40;&#41;«Трансакт-СЗЛ»](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [Просмотры каталогов безопасности &#40;&#41;Transact-S'L](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;&#41;"Трансакт-СЗЛ"](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
