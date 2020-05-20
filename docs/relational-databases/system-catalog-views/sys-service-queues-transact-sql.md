---
title: sys. service_queues (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.service_queues
- service_queues
- service_queues_TSQL
- sys.service_queues_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_queues catalog view
ms.assetid: 9fd9fa76-6128-410c-896f-741e6050143a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f0ffcc306a6b8194aeadcaa473e6eb981e7b97cf
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82834046"
---
# <a name="sysservice_queues-transact-sql"></a>sys.service_queues (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого объекта в базе данных, который является очередью обслуживания, с **sys. objects. Type** = sq.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**\<наследуемые столбцы>**||Список столбцов, наследуемых этим представлением, см. в разделе [sys. objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**max_readers**|**smallint**|Максимальное количество параллельных чтений, допустимых для очереди.|  
|**activation_procedure**|**nvarchar (776)**|Трехсоставное имя для процедуры активации.|  
|**execute_as_principal_id**|**int**|ID-идентификатор участника базы данных, указанного в инструкции EXECUTE AS.<br /><br /> По умолчанию и в случае EXECUTE AS CALLER имеет значение NULL.<br /><br /> ИДЕНТИФИКАТОР указанного участника, если он выполняется как \< основной>.<br /><br /> -2 = EXECUTE AS OWNER.|  
|**is_activation_enabled**|**bit**|1 = Активация разрешена.|  
|**is_receive_enabled**|**bit**|1 = Прием разрешен.|  
|**is_enqueue_enabled**|**bit**|1 = Разрешена постановка в очередь.|  
|**is_retention_enabled**|**bit**|1 = Сообщения хранятся до закрытия диалогового окна.|  
|**is_poison_message_handling_enabled**|**bit**|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.<br /><br /> 1 = обработка сообщений о сбое включена.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
