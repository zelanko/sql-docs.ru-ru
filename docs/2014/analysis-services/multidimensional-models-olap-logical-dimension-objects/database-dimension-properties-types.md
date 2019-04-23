---
title: Типы измерений | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- time dimensions [Analysis Services]
- quantitative dimensions [Analysis Services]
- BillOfMaterials dimension [Analysis Services]
- geography dimensions
- utility dimensions [Analysis Services]
- channel dimensions
- dimensions [Analysis Services], types
- products dimensions [Analysis Services]
- account dimensions [Analysis Services]
- organization dimensions
- currency dimensions [Analysis Services]
- rates dimensions
- promotion dimensions
- scenario dimensions [Analysis Services]
- customers dimensions [Analysis Services]
- Type property
ms.assetid: bd3195da-e762-4c98-b643-34c76e842343
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cbe1c8932c082ce537cd5dc3f2b12d98c05c3811
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60158000"
---
# <a name="dimension-types"></a>Типы измерений
  Настройка свойства `Type` предоставляет данные о содержимом измерения серверу и клиентским приложениям. В некоторых случаях настройка `Type` предоставляет клиентским приложениям только справочные сведения и является необязательной. В других случаях, например для измерений `Accounts` или `Time`, настройка свойства `Type` для измерения и его атрибутов определяет конкретные режимы, относящиеся к серверу, и может быть необходимой для реализации определенных режимов куба. Например, для свойства `Type` измерения можно установить значение `Accounts`, тем самым указывая клиентским приложениям, что в стандартном измерении содержатся атрибуты счетов.  Дополнительные сведения о времени, счетов и измерениях валют см. в разделе [Создание измерения типа Date](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [Создание учетной записи Finance с измерением типа родители потомки](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md), и [Создание валюты Введите измерения](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).  
  
 Настройка по умолчанию для типа измерения равна `Regular`, при этом не делаются никакие предположения в отношении содержимого измерения. Эта настройка применяется по умолчанию для всех измерений при первоначальном определении измерения, если только при определении измерения с помощью мастера измерений не указывается измерение `Time`. Необходимо также оставить `Regular` как тип измерения, если мастер измерений не предоставляет список соответствующих типов для типов измерения.  
  
## <a name="available-dimension-types"></a>Доступные типы измерений  
 В следующей таблице описаны типы измерений, доступных в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Тип измерения|Описание|  
|--------------------|-----------------|  
|Regular|Измерение, тип которого не был изменен на специальный тип измерения. |  
|Time|Измерение, атрибуты которого представляют периоды времени, например годы, семестры, кварталы, месяцы и дни.|  
|Organization|Измерение, атрибуты которого представляют сведения об организации, например сотрудниках или филиалах.|  
|Geography|Измерение, атрибуты которого представляют географические сведения, например города или почтовые индексы.|  
|Измерение ведомости материалов|Измерение, атрибуты которого представляют сведения по описи или производственные данные, например списки деталей для изделий.|  
|Измерение счетов|Измерение, атрибуты которого представляют диаграмму счетов для финансовой отчетности.|  
|Заказчики|Измерение, атрибуты которого представляют сведения о заказчиках или контактные данные.|  
|Измерение продуктов|Измерение, атрибуты которого представляют сведения о продуктах.|  
|Сценарий|Измерение, атрибуты которого представляют сведения о планах или данные о стратегическом анализе.|  
|Количественное измерение|Измерение, атрибуты которого представляют количественные данные.|  
|Служебная программа|Измерение, атрибуты которого представляют прочие сведения.|  
|CURRENCY|Измерение, атрибуты которого содержат данные валюты и метаданные.|  
|Изменения курсов|Измерение, атрибуты которого представляют данные о курсе обмена валюты.|  
|Channel|Измерение, атрибуты которого представляют данные о каналах.|  
|Promotion|Измерение, атрибуты которого представляют сведения об акциях по продвижению.|  
  
## <a name="see-also"></a>См. также  
 [Создание измерения с помощью существующей таблицы](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md)   
 [Измерения (службы Analysis Services — многомерные данные)](dimensions-analysis-services-multidimensional-data.md)  
  
  
