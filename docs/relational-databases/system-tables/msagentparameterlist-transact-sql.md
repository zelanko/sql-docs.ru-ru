---
title: "MSagentparameterlist (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSagentparameterlist_TSQL
- MSagentparameterlist
dev_langs: TSQL
helpviewer_keywords: Msagentparameterlist system table
ms.assetid: 4ea571a0-078d-4e13-95ee-f3d4bbd4dfb2
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 60f13f390ec499a3cc6f8add79538ea6d2cb133d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="msagentparameterlist-transact-sql"></a>MSagentparameterlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSagentparameterlist** таблица содержит сведения о параметрах агента репликации и используется для указания параметров, которые могут быть установлены для данного типа агента. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**agent_type**|**tinyint**|Тип агента:<br /><br /> **1** = агент моментальных снимков.<br /><br /> **2** = агент чтения журнала.<br /><br /> **3** = агент распространителя.<br /><br /> **4** = агент слияния.<br /><br /> **9** = агент чтения очереди.|  
|**имя_параметра**|**sysname**|Имя действительного аргумента агента.|  
|**значение по умолчанию**|**nvarchar(4000)**|Значение по умолчанию для аргумента агента, причем NULL указывает на то, что такого значения не существует.|  
|**MIN_VALUE**|**int**|Устанавливает нижний предел для аргумента агента, причем NULL указывает на то, что нижнего предела нет.|  
|**MAX_VALUE**|**int**|Устанавливает верхний предел для аргумента агента, причем NULL указывает на то, что верхнего предела нет.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
