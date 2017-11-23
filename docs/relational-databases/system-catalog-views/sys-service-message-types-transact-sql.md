---
title: "sys.service_message_types (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
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
- sys.service_message_types
- service_message_types
- sys.service_message_types_TSQL
- service_message_types_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.service_message_types catalog view
ms.assetid: 6a38709a-60fe-46f6-89da-718f74f15600
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 866424b72b284479e2f9e1771ff62c5099cb7f71
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysservicemessagetypes-transact-sql"></a>sys.service_message_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Это представление каталога содержит по строке на каждый тип сообщений, зарегистрированный в компоненте Service Broker.
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя типа сообщений, уникальное в пределах базы данных. Не допускает значения NULL.|  
|**message_type_id**|**int**|Идентификатор типа сообщений, уникальный в пределах базы данных. Не допускает значения NULL.|  
|**principal_id**|**int**|Идентификатор владельца данного типа сообщений. Допускает значение NULL.|  
|**Проверка**|**char(2)**|Проверка, осуществляемая брокером перед отправкой сообщений данного типа. Не допускает значения NULL. Может принимать одно из следующих значений.<br /><br /> N = нет<br /><br /> X = XML<br /><br /> E = пустая|  
|**validation_desc**|**nvarchar(60)**|Описание проверки, осуществляемой брокером перед отправкой сообщений данного типа. Допускает значение NULL. Может принимать одно из следующих значений.<br /><br /> None<br /><br /> XML<br /><br /> EMPTY|  
|**xml_collection_id**|**int**|Если для проверки используется схема XML, — идентификатор используемой коллекции схем.<br /><br /> В противном случае — значение NULL.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
