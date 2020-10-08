---
description: sys.database_usage (база данных SQL Azure)
title: sys.database_usage (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
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
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: f0c8809138bfad5cc9b7c4866978e7f2c111e09a
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2020
ms.locfileid: "91809213"
---
# <a name="sysdatabase_usage-azure-sql-database"></a>sys.database_usage (база данных SQL Azure)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  **Примечание. Это относится только к версии 11 базы данных SQL Azure.**  
  
 Содержит число, тип и длительность баз данных на [!INCLUDE[ssSDS](../../includes/sssds-md.md)] сервере.  
  
 Представление **sys.database_usage** содержит следующие столбцы.  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|time|Дата возникновения событий использования.|  
|sku|Тип уровня служб для базы данных: **Web**, **Business**, **Basic**, **Standard**, **Premium**|  
|quantity|Максимальное число баз данных номера SKU, который существовал в течение этого дня.|  
  
## <a name="permissions"></a>Разрешения  
 Доступ только для чтения к этому представлению доступен всем пользователям с разрешениями на подключение к базе данных **master** .  
  
## <a name="remarks"></a>Комментарии  
 Представление **sys.database_usage** возвращает по одной строке для каждого дня подписки.  
  
## <a name="see-also"></a>См. также:  
 [Сведения о ценах на базу данных SQL](https://go.microsoft.com/fwlink/?LinkID=394978)   
 [Учетные записи и выставление счетов в базе данных SQL Azure](/previous-versions/azure/ee621788(v=azure.100))  
  
