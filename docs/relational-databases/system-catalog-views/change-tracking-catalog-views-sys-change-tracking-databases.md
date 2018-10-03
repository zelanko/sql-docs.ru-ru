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
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5eb810817929132bfef67c543ddcb915852f923a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637742"
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
  
  
