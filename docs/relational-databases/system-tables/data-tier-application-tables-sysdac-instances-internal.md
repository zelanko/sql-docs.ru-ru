---
title: sysdac_instances_internal (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdac_instances_internal_TSQL
- sysdac_instances_internal
dev_langs:
- TSQL
helpviewer_keywords:
- sysdac_instances_internal
ms.assetid: d2d52cc4-3463-431a-b779-6fbfdeee1dfc
author: stevestein
ms.author: sstein
ms.openlocfilehash: e8cec14e22779391d954b2a666782e8783f50f3a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68084744"
---
# <a name="data-tier-application-tables---sysdac_instances_internal"></a>Таблицы приложений уровня данных — sysdac_instances_internal
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает по одной строке для каждого экземпляра приложения уровня данных (DAC), развернутого на экземпляре [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Эта таблица хранится в схеме dbo в базе данных msdb.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|instance_id|**UNIQUEIDENTIFIER**|Идентификатор экземпляра DAC.|  
|имя_экземпляра|**имеет sysname**|Имя экземпляра DAC, указанное при развертывании экземпляра.|  
|type_name|**имеет sysname**|Имя DAC, указанное при создании пакета DAC.|  
|type_version|**nvarchar (64)**|Версия DAC, указанная при создании пакета DAC.|  
|description|**nvarchar (4000)**|Описание DAC, записанное при создании пакета DAC.|  
|type_stream|**varbinary(max)**|Битовый поток, содержащий закодированное представление логических объектов (например, таблиц и представлений), которые содержатся в DAC.|  
|date_created|**datetime**|Дата и время создания экземпляра DAC.|  
|created_by|**имеет sysname**|Имя входа, создавшее экземпляр DAC.|  
  
## <a name="remarks"></a>Remarks  
 Доступ только для чтения к этому представлению доступен всем пользователям с разрешениями на подключение к базе данных master.  
  
## <a name="permissions"></a>Разрешения  
 Требует членства в предопределенной роли сервера sysadmin.  
  
## <a name="see-also"></a>См. также:  
 [Приложения уровня данных](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [dbo. sysdac_instances &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md)  
  
  
