---
title: "sys.resource_usage (база данных SQL Azure) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.resource_usage_TSQL
- resource_usage
- sys.resource_usage
- resource_usage_TSQL
dev_langs: TSQL
helpviewer_keywords:
- resource_usage
- sys.resource_usage
ms.assetid: b90147a3-fd8e-408e-961d-5c7000e068ad
caps.latest.revision: "15"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 48a5b1046abf347c5a1239bbcd07c96da4476d98
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysresourceusage-azure-sql-database"></a>sys.resource_usage (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  Этот компонент доступен в состоянии предварительной версии. Не полагайтесь на конкретную реализацию этого компонента, так как он может быть изменен или удален в следующей версии.  
>   
>  В предварительной версии группа эксплуатации [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] может отключать и включать сбор данных для данного динамического административного представления:  
>   
>  -   Если сбор данных включен, представление DMV возвращает текущие данные в том виде, в каком они были собраны.  
> -   Если сбор данных включен, представление DMV возвращает данные предыстории, которые могут устареть.  
  
 Предоставляет почасовые сводные данные по использованию ресурсов для пользовательских баз данных на текущем сервере. Данные предыстории хранятся в течение 90 дней.  
  
 Для каждой пользовательской базы данных существует одна строка для каждого часа в непрерывном формате. Даже если база данных не использовалась в течение этого часа, для него существует соответствующая строка, а значение usage_in_seconds для этой базы данных будет равно 0. Сведения об использовании хранилища и номере SKU добавляются для часа соответствующим образом.  
  
|Столбцы|Тип данных|Description|  
|-------------|---------------|-----------------|  
|time|**datetime**|Время (UTC) в почасовых приращениях.|  
|database_name|**nvarchar**|Имя пользовательской базы данных.|  
|sku|**nvarchar**|Имя SKU. Допустимы следующие значения:<br /><br /> Web Edition<br /><br /> Business Edition<br /><br /> Basic<br /><br /> Standard Edition<br /><br /> Premium|  
|usage_in_seconds|**int**|Время ЦП, использованное в течение часа.<br /><br /> Примечание: Этот столбец является устаревшим для V11 и не относится к версии 12. **Значение всегда равно 0.**|  
|storage_in_megabytes|**decimal**|Максимальный объем хранилища в течение часа, включающий данные базы данных, индексы, хранимые процедуры и метаданные.|  
  
## <a name="permissions"></a>Permissions  
 Это представление доступно для всех ролей пользователей с разрешениями на подключение к виртуальной **master** базы данных.  
  
  
