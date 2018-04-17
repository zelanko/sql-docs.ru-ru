---
title: sys.syscurconfigs (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.syscurconfigs
- sys.syscurconfigs_TSQL
- syscurconfigs
- syscurconfigs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.syscurconfigs compatibility view
- syscurconfigs system table
ms.assetid: 454ab849-07a5-4b50-ba0a-6b1b14721f77
caps.latest.revision: 34
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b691a8f107ab0ff5c20e8835d1f3f40f551ed78c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="syssyscurconfigs-transact-sql"></a>sys.syscurconfigs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит записи для каждого параметра текущей конфигурации. Также это представление содержит четыре записи, которые описывают структуру конфигурации. **syscurconfigs** строится динамически при запросе пользователем. Дополнительные сведения см. в разделе [sys.sysconfigures &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysconfigures-transact-sql.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**value**|**int**|Значение переменной, доступное для изменения пользователем. Оно используется компонентом [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], только если была выполнена инструкция RECONFIGURE.|  
|**Конфигурации**|**smallint**|Номер переменной конфигурации.|  
|**Комментарий**|**nvarchar(255)**|Описание параметра конфигурации.|  
|**status**|**smallint**|Битовая карта, показывающая состояние параметра. Возможные значения:<br /><br /> 0 = статический. Настройка вступает в силу после перезапуска сервера.<br /><br /> 1 = динамический. Переменная вступает в силу после выполнения инструкции RECONFIGURE.<br /><br /> 2 = расширенный. Переменная показывается только если **Показывать дополнительные параметры** имеет значение.<br /><br /> 3 = расширенный динамический.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
