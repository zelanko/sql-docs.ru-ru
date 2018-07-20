---
title: MSmerge_settingshistory (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_settingshistory
- MSmerge_settingshistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_settingshistory system table
ms.assetid: 0bdf2d5f-5502-44cd-aa9d-2d5006ad20ce
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 61d69b6a6c6c965e5737d185c0e4b936fea797fc
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102132"
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
  
  
