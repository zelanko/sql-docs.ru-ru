---
title: sys. сискурконфигс (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1b0fad344831d8073badb2618eb2c34a1cdc2161
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68089178"
---
# <a name="syssyscurconfigs-transact-sql"></a>sys.syscurconfigs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит записи для каждого параметра текущей конфигурации. Также это представление содержит четыре записи, которые описывают структуру конфигурации. **сискурконфигс** создается динамически при запросе пользователя. Дополнительные сведения см. в разделе [sys. sysconfigures &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysconfigures-transact-sql.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**значений**|**int**|Значение переменной, доступное для изменения пользователем. Оно используется компонентом [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], только если была выполнена инструкция RECONFIGURE.|  
|**файле**|**smallint**|Номер переменной конфигурации.|  
|**Метки**|**nvarchar(255)**|Описание параметра конфигурации.|  
|**состояние**|**smallint**|Битовая карта, показывающая состояние параметра. Возможные значения:<br /><br /> 0 = статический. Настройка вступает в силу после перезапуска сервера.<br /><br /> 1 = динамический. Переменная вступает в силу после выполнения инструкции RECONFIGURE.<br /><br /> 2 = расширенный. Переменная отображается, только если задан параметр **Показать дополнительные параметры** .<br /><br /> 3 = расширенный динамический.|  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление системных таблиц с системными представлениями &#40;&#41;Transact-SQL](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
