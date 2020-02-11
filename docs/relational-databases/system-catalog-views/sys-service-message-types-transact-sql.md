---
title: sys. service_message_types (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 560ee8a4ccc03f747df2b475394af092db589e7c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078739"
---
# <a name="sysservice_message_types-transact-sql"></a>sys.service_message_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Это представление каталога содержит по строке на каждый тип сообщений, зарегистрированный в компоненте Service Broker.
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**имеет sysname**|Имя типа сообщений, уникальное в пределах базы данных. Не допускает значения NULL.|  
|**message_type_id**|**int**|Идентификатор типа сообщений, уникальный в пределах базы данных. Не допускает значения NULL.|  
|**principal_id**|**int**|Идентификатор владельца данного типа сообщений. Допускает значение NULL.|  
|**проверки**|**char (2)**|Проверка, осуществляемая брокером перед отправкой сообщений данного типа. Не допускает значения NULL. Одно из двух значений:<br /><br /> N = нет<br /><br /> X = XML<br /><br /> E = пустая|  
|**validation_desc**|**nvarchar (60)**|Описание проверки, осуществляемой брокером перед отправкой сообщений данного типа. Допускает значение NULL. Одно из двух значений:<br /><br /> None<br /><br /> XML<br /><br /> EMPTY|  
|**xml_collection_id**|**int**|Если для проверки используется схема XML, — идентификатор используемой коллекции схем.<br /><br /> В противном случае — значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Дополнительные сведения см. в разделе [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
