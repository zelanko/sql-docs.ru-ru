---
title: sys. service_contract_message_usages (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- service_contract_message_usages_TSQL
- sys.service_contract_message_usages
- sys.service_contract_message_usages_TSQL
- service_contract_message_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_contract_message_usages catalog view
ms.assetid: f783e662-126c-4595-8e22-f9d05191f5d0
author: stevestein
ms.author: sstein
ms.openlocfilehash: bca839c61a59c69a7f6cf7e659ad940864fcee37
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68132931"
---
# <a name="sysservice_contract_message_usages-transact-sql"></a>sys.service_contract_message_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Данное представление каталога содержит по одной строке для каждой пары (контракт, тип сообщения).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**service_contract_id**|**int**|Идентификатор контракта, использующего тип сообщения. Не допускает значения NULL.|  
|**message_type_id**|**int**|Идентификатор типа сообщения, используемого контрактом. Не допускает значения NULL.|  
|**is_sent_by_initiator**|**bit**|Тип сообщения может быть отправлен инициатором диалога. Не допускает значения NULL.|  
|**is_sent_by_target**|**bit**|Тип сообщения может быть отправлен вторым участником диалога. Не допускает значения NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
