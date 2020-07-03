---
title: sys.sysперфинфо (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysperfinfo_TSQL
- sys.sysperfinfo_TSQL
- sys.sysperfinfo
- sysperfinfo
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysperfinfo compatibility view
- sysperfinfo system table
ms.assetid: e22a81cd-27de-4690-9443-6aad6393bd3c
author: rothja
ms.author: jroth
ms.openlocfilehash: a2cdadb112dbceb6a3b031707b8ba8b889bad822
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85895850"
---
# <a name="syssysperfinfo-transact-sql"></a>sys.sysperfinfo (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Содержит [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] представление внутренних счетчиков производительности, которые могут отображаться в системном мониторе Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_name**|**nchar (128)**|Имя объекта производительности, например **SQLServer: локкманажер** или **SQLServer: буфферманажер**.|  
|**counter_name**|**nchar (128)**|Имя счетчика производительности в объекте, например **запрошенных** **запросов страниц** или блокировок.|  
|**instance_name**|**nchar (128)**|Именованный экземпляр счетчика. Например, существуют счетчики для каждого типа блокировки, такие как **Таблица**, **страница**, **ключ**и т. д. Имя экземпляра позволяет различать похожие счетчики.|  
|**cntr_value**|**bigint**|Текущее значение счетчика. Часто оно является счетчиком уровня или счетчиком монотонно возрастающей величины, подсчитывающей наступление событий экземпляра.|  
|**cntr_type**|**int**|Тип счетчика, как определено архитектурой производительности Windows.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;&#41;Transact-SQL](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
