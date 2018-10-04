---
title: sys.cryptographic_providers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cryptographic_providers
- sys.cryptographic_providers
- sys.cryptographic_providers_TSQL
- cryptographic_providers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.cryptographic_providers catalog view
ms.assetid: 9da0da95-792e-48b4-9f60-47f0729c279c
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 80918c74613e0fb608a9d48c1e56ad2cf206b06e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47791242"
---
# <a name="syscryptographicproviders-transact-sql"></a>sys.cryptographic_providers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает одну строку для каждого зарегистрированного поставщика служб шифрования.  
    
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**provider_id**|**int**|Идентификационный номер поставщика служб шифрования.|  
|**name**|**sysname**|Имя поставщика служб шифрования.|  
|**Идентификатор GUID**|**uniqueidentifier**|Глобальный уникальный идентификатор поставщика (GUID).|  
|**version**|**nvarchar(50)**|Версия поставщика в формате "*aa.bb.cccc.dd*".|  
|**dll_path**|**nvarchar(512)**|Путь к библиотеке DLL, реализующей API-интерфейс расширенного управления ключами.|  
|**is_enabled**|**bit**|Указывает, включен ли поставщик на сервере или нет:<br /><br /> 0 = не включен (по умолчанию);<br /><br /> 1 = включен|  
  
## <a name="remarks"></a>Примечания  
 **Sys.cryptographic_providers** представление роли public.  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Расширенное управление ключами (EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)  
  
  
