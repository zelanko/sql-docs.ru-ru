---
title: sysdac_instances_internal (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdac_instances_internal_TSQL
- sysdac_instances_internal
dev_langs:
- TSQL
helpviewer_keywords:
- sysdac_instances_internal
ms.assetid: d2d52cc4-3463-431a-b779-6fbfdeee1dfc
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5389e86dee17cd4a8a4e5432e98d7c5a554c1469
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="data-tier-application-tables---sysdacinstancesinternal"></a>Таблицы приложения уровня данных — sysdac_instances_internal
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает по одной строке для каждого экземпляра приложения уровня данных (DAC), развернутого на экземпляре [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Эта таблица хранится в схеме dbo в базе данных msdb.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|instance_id|**uniqueidentifier**|Идентификатор экземпляра DAC.|  
|имя_экземпляра|**sysname**|Имя экземпляра DAC, указанное при развертывании экземпляра.|  
|type_name|**sysname**|Имя DAC, указанное при создании пакета DAC.|  
|type_version|**nvarchar(64)**|Версия DAC, указанная при создании пакета DAC.|  
|description|**nvarchar(4000)**|Описание DAC, записанное при создании пакета DAC.|  
|type_stream|**varbinary(max)**|Битовый поток, содержащий закодированное представление логических объектов (например, таблиц и представлений), которые содержатся в DAC.|  
|date_created|**datetime**|Дата и время создания экземпляра DAC.|  
|created_by|**sysname**|Имя входа, создавшее экземпляр DAC.|  
  
## <a name="remarks"></a>Замечания  
 Доступ только для чтения к этому представлению доступен всем пользователям с разрешениями на подключение к базе данных master.  
  
## <a name="permissions"></a>Разрешения  
 Требует членства в предопределенной роли сервера sysadmin.  
  
## <a name="see-also"></a>См. также  
 [Приложения уровня данных](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [dbo.sysdac_instances &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md)  
  
  
