---
title: sys.database_usage (база данных SQL Azure) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- database_usage
- database_usage_TSQL
- sys.database_usage_TSQL
- sys.database_usage
dev_langs:
- TSQL
helpviewer_keywords:
- database_usage
- sys.database_usage
ms.assetid: be6820de-60bf-4ddd-ace7-4077893d630f
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: cbfb195c316dee403c307c90d50ef4f882f38abf
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdatabaseusage-azure-sql-database"></a>sys.database_usage (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  **Примечание: Это относится только к V11 базы данных SQL Azure.**  
  
 Возвращает количество, тип и длительность существования баз данных на [!INCLUDE[ssSDS](../../includes/sssds-md.md)] сервера.  
  
 **Sys.database_usage** представление содержит следующие столбцы.  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|time|Дата возникновения событий использования.|  
|sku|Тип уровня обслуживания для базы данных: **Web**, **Business**, **основные**, **Стандартная**, **Premium**|  
|quantity|Максимальное число баз данных номера SKU, который существовал в течение этого дня.|  
  
## <a name="permissions"></a>Разрешения  
 Доступ только для чтения к этому представлению доступен для всех пользователей с разрешениями на подключение к **master** базы данных.  
  
## <a name="remarks"></a>Замечания  
 **Sys.database_usage** представление возвращает по одной строке для каждого дня подписки.  
  
## <a name="see-also"></a>См. также  
 [Сведения о ценах базы данных SQL](http://go.microsoft.com/fwlink/?LinkID=394978)   
 [Учетные записи и выставление счетов в базе данных Azure SQL для Windows](http://msdn.microsoft.com/library/windowsazure/ee621788.aspx)  
  
  
