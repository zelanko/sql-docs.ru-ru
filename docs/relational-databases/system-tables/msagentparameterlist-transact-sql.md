---
title: MSagentparameterlist (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSagentparameterlist_TSQL
- MSagentparameterlist
dev_langs:
- TSQL
helpviewer_keywords:
- Msagentparameterlist system table
ms.assetid: 4ea571a0-078d-4e13-95ee-f3d4bbd4dfb2
author: stevestein
ms.author: sstein
ms.openlocfilehash: d0ba22c75e36cc927fbd923af25aad48b3d02801
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119252"
---
# <a name="msagentparameterlist-transact-sql"></a>MSagentparameterlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSagentparameterlist** таблица содержит сведения о параметрах агента репликации и используется для указания параметров, которые могут быть установлены для данного типа агента. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**agent_type**|**tinyint**|Тип агента:<br /><br /> **1** = агент моментальных снимков.<br /><br /> **2** = агент чтения журнала.<br /><br /> **3** = агент распространителя.<br /><br /> **4** = агент слияния.<br /><br /> **9** = агент чтения очереди.|  
|**parameter_name**|**sysname**|Имя действительного аргумента агента.|  
|**default_value**|**nvarchar(4000)**|Значение по умолчанию для аргумента агента, причем NULL указывает на то, что такого значения не существует.|  
|**MIN_VALUE**|**int**|Устанавливает нижний предел для аргумента агента, причем NULL указывает на то, что нижнего предела нет.|  
|**MAX_VALUE**|**int**|Устанавливает верхний предел для аргумента агента, причем NULL указывает на то, что верхнего предела нет.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
