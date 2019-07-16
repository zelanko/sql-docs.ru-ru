---
title: sys.change_tracking_databases (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9d3f2f92e9be7b6d4f38edff7cb36aa67e055788
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68136537"
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
 [Представления каталога отслеживания изменений &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/6e8fd949-5560-4b34-879f-4e25aa24b183)   
 [Отслеживание измененных данных (SQL Server)](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
