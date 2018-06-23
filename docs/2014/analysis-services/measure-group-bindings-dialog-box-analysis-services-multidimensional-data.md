---
title: Диалоговое окно «привязки группы мер» (службы Analysis Services — многомерные данные) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubeeditor.dimensionusage.definerelationship.measuregroupbindings.f1
helpviewer_keywords:
- Measure Group Bindings dialog box
ms.assetid: ed642780-5350-438e-af73-b9ceab3f876d
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1508624a9d0e5a9f36c8ec7c15093f56b37977ea
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192565"
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
 [Определение связи диалоговое окно &#40;службы Analysis Services — многомерные данные&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md)   
 [Конструкторы и диалоговые окна служб Analysis Services &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  