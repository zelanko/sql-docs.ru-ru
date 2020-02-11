---
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: cc1e0915fb48b42429bb2821476f98154ac39451
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68005100"
---
# <a name="sysdm_cryptographic_provider_properties-transact-sql"></a>sys.dm_cryptographic_provider_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о зарегистрированных поставщиках служб шифрования.  
  
 
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|provider_id|**int**|Идентификационный номер поставщика служб шифрования.|  
|guid|**UNIQUEIDENTIFIER**|Глобальный уникальный идентификатор поставщика (GUID).|  
|provider_version|**nvarchar(256)**|Версия поставщика в формате "*AA.BB.CCCC.dd*".|  
|sqlcrypt_version|**nvarchar(256)**|Основной номер версии API [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] шифрования в формате "*AA.BB.CCCC.dd*".|  
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
 [Представления каталога безопасности &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Расширенное управление ключами &#40;управления РАСШИРЕНным ключом&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [Динамические административные представления и функции, связанные с безопасностью &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
