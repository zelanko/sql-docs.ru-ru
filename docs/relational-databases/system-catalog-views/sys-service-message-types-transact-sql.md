---
title: sys.service_message_types (Transact-SQL) | Документы Microsoft
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
- sys.service_message_types
- service_message_types
- sys.service_message_types_TSQL
- service_message_types_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_message_types catalog view
ms.assetid: 6a38709a-60fe-46f6-89da-718f74f15600
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 15482ba9ddf58f4b037cb19ee376df224308516d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysservicemessagetypes-transact-sql"></a>sys.service_message_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Это представление каталога содержит по строке на каждый тип сообщений, зарегистрированный в компоненте Service Broker.
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя типа сообщений, уникальное в пределах базы данных. Не допускает значения NULL.|  
|**message_type_id**|**int**|Идентификатор типа сообщений, уникальный в пределах базы данных. Не допускает значения NULL.|  
|**principal_id**|**int**|Идентификатор владельца данного типа сообщений. Допускает значение NULL.|  
|**Проверка**|**char(2)**|Проверка, осуществляемая брокером перед отправкой сообщений данного типа. Не допускает значения NULL. Может принимать одно из следующих значений.<br /><br /> N = нет<br /><br /> X = XML<br /><br /> E = пустая|  
|**validation_desc**|**nvarchar(60)**|Описание проверки, осуществляемой брокером перед отправкой сообщений данного типа. Допускает значение NULL. Может принимать одно из следующих значений.<br /><br /> None<br /><br /> XML<br /><br /> EMPTY|  
|**xml_collection_id**|**int**|Если для проверки используется схема XML, — идентификатор используемой коллекции схем.<br /><br /> В противном случае — значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
