---
title: sys.change_tracking_databases (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- change_tracking_databases
- sys.change_tracking_databases_TSQL
- sys.change_tracking_databases
- change_tracking_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.change_tracking_databases
- change tracking [SQL Server], sys.change_tracking_databases
ms.assetid: bb233baa-2991-4904-a0eb-3772b81121a4
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a3ec7102bbbdc01694bea11911d0de9a89dbacc8
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38049672"
---
# <a name="change-tracking-catalog-views---syschangetrackingdatabases"></a>Изменение представления каталога отслеживания - sys.change_tracking_databases
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Возвращает одну строку для каждой базы данных, для которой включено отслеживание изменений.  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор базы данных. Он уникален в рамках экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|is_auto_cleanup_on|**bit**|Указывает, предусмотрена ли автоматическая очистка данных отслеживания изменений по истечении заданного срока хранения:<br /><br /> 0 = Выключена;<br /><br /> 1 = Включена.|  
|retention_period|**int**|Если используется автоматическая очистка, сроком хранения определяется продолжительность хранения данных отслеживания изменений в базе данных.|  
|retention_period_units_desc|**nvarchar(60)**|Задает описание срока хранения:<br /><br /> Минуты<br /><br /> Часы<br /><br /> Дни|  
|retention_period_units|**tinyint**|Единица времени для срока хранения:<br /><br /> 1 = Минуты;<br /><br /> 2 = Часы;<br /><br /> 3 = Дни.|  
  
## <a name="permissions"></a>Разрешения  
 Та же проверка разрешений видит sys.change_tracking_databases при внесении для sys.databases. Если вызывающий объект, использующий представление sys.change_tracking_databases, не является владельцем базы данных, минимальные разрешения, необходимые для просмотра соответствующей строки являются ALTER ANY DATABASE или разрешение уровня сервера VIEW ANY DATABASE или разрешение CREATE DATABASE в базе данных master База данных или текущей базы данных.  
  
## <a name="see-also"></a>См. также  
 [Представления каталога отслеживания изменений &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/6e8fd949-5560-4b34-879f-4e25aa24b183)   
 [Отслеживание измененных данных (SQL Server)](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
