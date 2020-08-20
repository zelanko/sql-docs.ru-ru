---
description: sys.dm_cryptographic_provider_properties (Transact-SQL)
title: sys. dm_cryptographic_provider_properties (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_cryptographic_provider_properties_TSQL
- sys.dm_cryptographic_provider_properties
- sys.dm_cryptographic_provider_properties_TSQL
- dm_cryptographic_provider_properties
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_properties dynamic management view
ms.assetid: 024b0095-6766-4189-a39a-d316c5ec2874
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 562c2884b0eda3488b436c1007c188ec7c64425b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493797"
---
# <a name="sysdm_cryptographic_provider_properties-transact-sql"></a>sys.dm_cryptographic_provider_properties (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает сведения о зарегистрированных поставщиках служб шифрования.  
  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|provider_id|**int**|Идентификационный номер поставщика служб шифрования.|  
|guid|**uniqueidentifier**|Глобальный уникальный идентификатор поставщика (GUID).|  
|provider_version|**nvarchar(256)**|Версия поставщика в формате "*AA.BB.CCCC.dd*".|  
|sqlcrypt_version|**nvarchar(256)**|Основной номер версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] API шифрования в формате "*AA.BB.CCCC.dd*".|  
|friendly_name|**nvarchar (2048)**|Имя введено поставщиком.|  
|authentication_type|**nvarchar(256)**|WINDOWS, BASIC или OTHER.|  
|symmetric_key_support|**tinyint**|0 (не поддерживается)<br /><br /> 1 (поддерживается)|  
|symmetric_key_export|**tinyint**|0 (не поддерживается)<br /><br /> 1 (поддерживается)|  
|symmetric_key_import|**tinyint**|0 (не поддерживается)<br /><br /> 1 (поддерживается)|  
|symmetric_key_persistance|**tinyint**|0 (не поддерживается)<br /><br /> 1 (поддерживается)|  
|asymmetric_key_support|**tinyint**|0 (не поддерживается)<br /><br /> 1 (поддерживается)|  
|asymmetric_key_export|**tinyint**|0 (не поддерживается)<br /><br /> 1 (поддерживается)|  
|symmetric_key_import|**tinyint**|0 (не поддерживается)<br /><br /> 1 (поддерживается)|  
|symmetric_key_persistance|**tinyint**|0 (не поддерживается)<br /><br /> 1 (поддерживается)|  
  
## <a name="remarks"></a>Remarks  
 Представление sys.dm_cryptographic_provider_properties доступно для роли public.  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Расширенное управление ключами (EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [Динамические представления управления и функции, связанные с безопасностью (Transact-SQL)](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
