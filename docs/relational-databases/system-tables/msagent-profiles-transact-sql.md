---
title: MSagent_profiles (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSagent_profiles
- MSagent_profiles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSagent_profiles system table
ms.assetid: 4ab1b2ae-b6d9-42b7-9b31-98547dbb7f99
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0e6aa2b9a506f0ad485c4a0eb4dc16960ae44d2a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832360"
---
# <a name="msagent_profiles-transact-sql"></a>MSagent_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **MSagent_profiles** содержит по одной строке для каждого определенного профиля агента репликации. Эта таблица хранится в базе данных **msdb** .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|Идентификатор профиля.|  
|**profile_name**|**sysname**|Уникальное имя профиля для типа агента.|  
|**agent_type**|**int**|Тип агента:<br /><br /> **1** = агент моментальных снимков<br /><br /> **2** = агент чтения журнала<br /><br /> **3** = агент распространения<br /><br /> **4** = агент слияния<br /><br /> **9** = агент чтения очереди|  
|**type**|**int**|Тип профиля:<br /><br /> **0** = система**1** = настраиваемая|  
|**nописание**|**nvarchar (3000)**|Описание профиля.|  
|**def_profile**|**bit**|Указывает на использование профиля по умолчанию для данного типа агента.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
