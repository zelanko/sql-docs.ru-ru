---
title: sys. sysconfigures (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysconfigures
- sysconfigures
- sys.sysconfigures_TSQL
- sysconfigures_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysconfigures compatibility view
- sysconfigures system table
ms.assetid: 146bf10a-c898-4676-a2a1-673fb1cee7a2
author: rothja
ms.author: jroth
ms.openlocfilehash: c785ee1c4d3c5382aa42adf48ad9880f00297137
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68089206"
---
# <a name="syssysconfigures-transact-sql"></a>sys.sysconfigures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого установленного пользователем параметра конфигурации. **sysconfigures** содержит параметры конфигурации, которые определены до последнего запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также любые динамические параметры конфигурации, заданные после этого.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**value**|**int**|Значение переменной, доступное для изменения пользователем. Оно используется компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)], только если была выполнена инструкция RECONFIGURE.|  
|**файле**|**int**|Номер переменной конфигурации.|  
|**Метки**|**nvarchar(255)**|Описание параметра конфигурации.|  
|**status**|**smallint**|Битовая карта, указывающая состояние параметра. Возможные значения:<br /><br /> 0 = статический. Настройка вступает в силу после перезапуска сервера.<br /><br /> 1 = динамический. Переменная вступает в силу после выполнения инструкции RECONFIGURE.<br /><br /> 2 = расширенный. Переменная отображается, только если задан параметр **Показать дополнительные параметры** . Настройка вступает в силу после перезапуска сервера.<br /><br /> 3 = расширенный динамический.|  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление системных таблиц с системными представлениями &#40;&#41;Transact-SQL](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
