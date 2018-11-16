---
title: sys.database_usage (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: f17e34de7c230b111652ea57a3baa072a442a6a5
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51656743"
---
# <a name="sysdatabaseusage-azure-sql-database"></a>sys.database_usage (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  **Примечание: Это относится только к базе данных SQL Azure версии 11.**  
  
 Выводит количество, тип и длительность существования баз данных на [!INCLUDE[ssSDS](../../includes/sssds-md.md)] сервера.  
  
 **Sys.database_usage** представление содержит следующие столбцы.  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|time|Дата возникновения событий использования.|  
|sku|Тип уровня службы для базы данных: **Web**, **бизнеса**, **основные**, **стандартный**, **уровня "премиум"**|  
|quantity|Максимальное число баз данных номера SKU, который существовал в течение этого дня.|  
  
## <a name="permissions"></a>Разрешения  
 Доступ только для чтения к этому представлению доступна для всех пользователей с разрешениями на подключение к **master** базы данных.  
  
## <a name="remarks"></a>Примечания  
 **Sys.database_usage** представление возвращает одну строку за каждый день вашей подписки.  
  
## <a name="see-also"></a>См. также  
 [Сведения о ценах на базы данных SQL](https://go.microsoft.com/fwlink/?LinkID=394978)   
 [Учетные записи и выставление счетов в базе данных Azure SQL для Windows](https://msdn.microsoft.com/library/windowsazure/ee621788.aspx)  
  
  
