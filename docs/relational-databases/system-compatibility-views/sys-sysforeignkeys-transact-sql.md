---
title: sys.sysфореигнкэйс (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysforeignkeys
- sys.sysforeignkeys
- sys.sysforeignkeys_TSQL
- sysforeignkeys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysforeignkeys system table
- sys.sysforeignkeys compatibility view
ms.assetid: 41544236-1c46-4501-be88-18c06963b6e8
author: rothja
ms.author: jroth
ms.openlocfilehash: fff6be675a0433b3e51df74086fba59b8772b8d7
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85901064"
---
# <a name="syssysforeignkeys-transact-sql"></a>sys.sysforeignkeys (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Содержит данные об ограничениях FOREIGN KEY, включенных в определения таблиц базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|Идентификатор ограничения FOREIGN KEY.|  
|**fkeyid**|**int**|Идентификатор объекта таблицы с ограничением FOREIGN KEY.|  
|**rkeyid**|**int**|Идентификатор объекта таблицы, на которую ссылается ограничение FOREIGN KEY.|  
|**fkey**|**smallint**|Идентификатор ссылающегося столбца.|  
|**rkey**|**smallint**|Идентификатор столбца, на который указывает ссылка.|  
|**keyno**|**smallint**|Положение столбца в списке ссылочных столбцов.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;&#41;Transact-SQL](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
