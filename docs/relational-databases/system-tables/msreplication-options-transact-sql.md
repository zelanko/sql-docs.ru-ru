---
description: MSreplication_options (Transact-SQL)
title: MSreplication_options (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSreplication_options
- MSreplication_options_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_options system table
ms.assetid: 23cf10d7-8bc1-4368-b5eb-e5576421e776
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 44099921a382ca05f0e2e379b2df9d97e1c28f6e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460351"
---
# <a name="msreplication_options-transact-sql"></a>MSreplication_options (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  В **MSreplication_options** таблице хранятся метаданные, которые используются для внутренних целей репликации. Эта таблица хранится в базе данных **master** .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**optname**|**sysname**|Только для внутреннего применения.|  
|**value**|**bit**|Только для внутреннего применения.|  
|**major_version**|**int**|Только для внутреннего применения.|  
|**minor_version**|**int**|Только для внутреннего применения.|  
|**редакции**|**int**|Только для внутреннего применения.|  
|**install_failures**|**int**|Только для внутреннего применения.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации (Transact-SQL)](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
