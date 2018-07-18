---
title: Диалоговое окно «привязки группы мер» (службы Analysis Services — многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.dimensionusage.definerelationship.measuregroupbindings.f1
helpviewer_keywords:
- Measure Group Bindings dialog box
ms.assetid: ed642780-5350-438e-af73-b9ceab3f876d
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2c306ba41e8ebb6fe2615be0bec8f3cebd560e65
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37226414"
---
# <a name="measure-group-bindings-dialog-box-analysis-services---multidimensional-data"></a>Диалоговое окно «Привязки группы мер» (службы Analysis Services — многомерные данные)
  Используйте диалоговое окно **Привязки группы мер** для создания и изменения прямых связей между негранулярными атрибутами в измерении куба и столбцами в группе мер для связи обычного измерения, а также для указания параметров обработки значений NULL любого из атрибутов в измерении куба из диалогового окна **Задание связи**.  
  
## <a name="options"></a>Параметры  
 **Таблица группы мер**  
 Отображает имя таблицы фактов для выбранной группы мер.  
  
 **Атрибуты**  
 Отображает сетку атрибутов и таблиц измерений. Выберите атрибут для создания или изменения свойств на панели **Связь** для выбранного атрибута. Сетка содержит следующие столбцы:  
  
|Параметр|Определение|  
|------------|----------------|  
|**Имя атрибута**|Показывает имя атрибута.|  
|**Таблица измерения**|Отображает имя таблицы измерений, на которой основан атрибут.|  
  
 **Связь**  
 Отображает сетку связей между столбцами таблицы измерений для выбранного атрибута и столбцами таблицы фактов для выбранной группы мер, а также параметр обработки NULL для связи. Сетка содержит следующие столбцы:  
  
|Параметр|Определение|  
|------------|----------------|  
|**Столбцы измерений**|Отображает столбцы таблицы измерений, на которой основан атрибут, выбранный на панели **Атрибуты** .|  
|**Столбцы группы мер**|Выберите параметр **Унаследован от измерения** , чтобы использовать связь группы мер, унаследованную от измерения, или столбец из таблицы фактов, на котором основана группа мер, чтобы явно определить связь.|  
|**Обработки значений NULL**|Выберите параметр обработки значения NULL ‎для атрибута. Дополнительные сведения о параметрах обработки значений NULL см. в разделе [Элемент NullProcessing (ASSL)](scripting/properties/nullprocessing-element-assl.md).|  
  
## <a name="see-also"></a>См. также  
 [Определите окно связи &#40;службы Analysis Services — многомерные данные&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md)   
 [Конструкторы и диалоговые окна служб Analysis Services &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
