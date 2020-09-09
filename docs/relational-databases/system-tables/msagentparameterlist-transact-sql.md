---
description: MSagentparameterlist (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b5fcded0e1ffe97578832f773e65d2d08e1c41d8
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551055"
---
# <a name="msagentparameterlist-transact-sql"></a>MSagentparameterlist (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSagentparameterlist** содержит сведения о параметрах агента репликации и используется для указания параметров, которые могут быть установлены для данного типа агента. Эта таблица хранится в базе данных **msdb** .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**agent_type**|**tinyint**|Тип агента:<br /><br /> **1** = агент моментальных снимков.<br /><br /> **2** = агент чтения журнала.<br /><br /> **3** = агент распространения.<br /><br /> **4** = агент слияния.<br /><br /> **9** = агент чтения очереди.|  
|**parameter_name**|**sysname**|Имя действительного аргумента агента.|  
|**default_value**|**nvarchar(4000)**|Значение по умолчанию для аргумента агента, причем NULL указывает на то, что такого значения не существует.|  
|**min_value**|**int**|Устанавливает нижний предел для аргумента агента, причем NULL указывает на то, что нижнего предела нет.|  
|**max_value**|**int**|Устанавливает верхний предел для аргумента агента, причем NULL указывает на то, что верхнего предела нет.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
