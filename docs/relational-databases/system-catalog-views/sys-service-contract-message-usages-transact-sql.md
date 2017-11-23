---
title: "sys.service_contract_message_usages (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- service_contract_message_usages_TSQL
- sys.service_contract_message_usages
- sys.service_contract_message_usages_TSQL
- service_contract_message_usages
dev_langs: TSQL
helpviewer_keywords: sys.service_contract_message_usages catalog view
ms.assetid: f783e662-126c-4595-8e22-f9d05191f5d0
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 011a54077a6b58420746e74ce7c39cfddaa7ffed
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysservicecontractmessageusages-transact-sql"></a>sys.service_contract_message_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Данное представление каталога содержит по одной строке для каждой пары (контракт, тип сообщения).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**service_contract_id**|**int**|Идентификатор контракта, использующего тип сообщения. Не допускает значения NULL.|  
|**message_type_id**|**int**|Идентификатор типа сообщения, используемого контрактом. Не допускает значения NULL.|  
|**is_sent_by_initiator**|**bit**|Тип сообщения может быть отправлен инициатором диалога. Не допускает значения NULL.|  
|**is_sent_by_target**|**bit**|Тип сообщения может быть отправлен вторым участником диалога. Не допускает значения NULL.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
