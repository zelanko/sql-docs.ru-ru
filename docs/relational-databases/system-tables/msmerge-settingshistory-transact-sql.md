---
title: MSmerge_settingshistory (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_settingshistory
- MSmerge_settingshistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_settingshistory system table
ms.assetid: 0bdf2d5f-5502-44cd-aa9d-2d5006ad20ce
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 25505e0b96c627feb51fd59abfe587851520b724
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63026560"
---
# <a name="msmergesettingshistory-transact-sql"></a>MSmerge_settingshistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_settingshistory** таблица используется для ведения журнала изменений, внесенных в свойства статьи и публикации для репликации слиянием, по одной строке для каждого изменения, внесенные в топологии репликации слиянием. Данная таблица также хранит сведения о том, когда были произведены исходные настройки свойств. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**eventtime**|**datetime**|Дата и время события.|  
|**pubid**|**uniqueidentifier**|Уникальный идентификатор данной публикации.|  
|**artid**|**uniqueidentifier**|Уникальный идентификационный номер данной статьи.|  
|**Тип события**|**tinyint**|Указывает тип зарегистрированного события, может принимать одно из следующих значений:<br /><br /> **1** — исходная установка свойства уровня публикации.<br /><br /> **2** -изменение в свойстве публикации.<br /><br /> **101** — исходная установка свойства статьи.<br /><br /> **102** -изменения в свойстве статьи.|  
|**propertyname**|**sysname**|Имя установленного или измененного свойства|  
|**значение previousvalue**|**sysname**|Предыдущее значение свойства, если свойство было изменено.|  
|**новое значение**|**sysname**|Значение, присвоенное свойству при изменении или при создании.|  
|**eventtext**|**nvarchar(2000)**|Символьная строка, описывающая событие.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
