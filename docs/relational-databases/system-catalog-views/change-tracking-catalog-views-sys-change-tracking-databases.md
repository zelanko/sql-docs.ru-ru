---
description: Отслеживание изменений представлений каталога sys.change_tracking_databases
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
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e586e44bf91623d0ffcbe1ba68a8fa483d3702b9
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97429659"
---
# <a name="change-tracking-catalog-views---syschange_tracking_databases"></a>Отслеживание изменений представлений каталога sys.change_tracking_databases
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает одну строку для каждой базы данных, для которой включено отслеживание изменений.  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор базы данных. Он уникален в рамках экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|is_auto_cleanup_on|**bit**|Указывает, предусмотрена ли автоматическая очистка данных отслеживания изменений по истечении заданного срока хранения:<br /><br /> 0 = Выключена;<br /><br /> 1 = Включена.|  
|retention_period|**int**|Если используется автоматическая очистка, сроком хранения определяется продолжительность хранения данных отслеживания изменений в базе данных.|  
|retention_period_units_desc|**nvarchar(60)**|Задает описание срока хранения:<br /><br /> Минуты<br /><br /> Часы<br /><br /> Дни|  
|retention_period_units|**tinyint**|Единица времени для срока хранения:<br /><br /> 1 = Минуты;<br /><br /> 2 = Часы;<br /><br /> 3 = Дни.|  
  
## <a name="permissions"></a>Разрешения  
 Для sys.change_tracking_databases выполняются те же проверки разрешений, что и для sys. databases. Если вызывающий объект sys.change_tracking_databases не является владельцем базы данных, то минимальными разрешениями, необходимыми для просмотра соответствующей строки, являются разрешения на уровне сервера ALTER ANY DATABASE или VIEW любое базу данных или разрешение CREATE DATABASE в базе данных master или текущей базе данных.  
  
## <a name="see-also"></a>См. также:  
 [Отслеживание изменений представления каталога &#40;&#41;Transact-SQL ](./catalog-views-transact-sql.md)   
 [Отслеживание измененных данных (SQL Server)](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
