---
title: Диалоговое окно «Свойства куба или модели» (SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.cubeproperties.f1
ms.assetid: 97e367f9-f95a-4163-add1-c74fd22db249
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6857ece2f81ffdba839ec1a7f0ef420ec5d0acdf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66086601"
---
# <a name="cube-or-model-properties-dialog-box-ssas"></a>Диалоговое окно «Свойства куба или модели» (SSAS)
  Используйте диалоговое окно **Свойства базы данных** в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] для установки свойств куба или шаблона базы данных. Чтобы вызвать это диалоговое окно, необходимо щелкнуть правой клавишей мыши куб или модель в **обозревателе объектов** и выбрать пункт **Свойства**.  
  
 Это диалоговое окно также содержит вкладки для следующих свойств:  
  
-   [Редактор формы действия отчета &#40;вкладка "действия", конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
-   [Конфигурация ошибок при обработке кубов, секций и измерений &#40;SSAS — многомерные&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)  
  
-   [Упреждающее кэширование &#40;диалоговое окно "Свойства секции"&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md)  
  
## <a name="options"></a>Параметры  
  
|Термин|Определение|  
|----------|----------------|  
|**Название**|Отображает имя куба или модели.|  
|**УДОСТОВЕРЕНИЯ**|Отображает идентификатор куба или модели.|  
|**Описание**|Отображает описание куба или модели.|  
|**Создать отметку времени**|Отображает дату и время создания куба или модели.|  
|**Последнее обновление схемы**|Отображает дату и время последнего обновления метаданных куба или модели.|  
|**Режим обработки кэша скриптов**|Выберите режим обработки, который следует использовать для кэша скриптов куба или модели. Дополнительные сведения о значениях этого свойства см. в разделе <xref:Microsoft.AnalysisServices.Cube.ScriptCacheProcessingMode%2A>.|  
|**Режим обработки**|Выберите режим обработки для указанного куба или модели. Дополнительные сведения о значениях этого свойства см. в разделе <xref:Microsoft.AnalysisServices.Cube.ProcessingMode%2A>.|  
|**Место хранения**|Введите имя папки, которая будет использоваться по умолчанию как место хранения для групп мер и секций, связанных с кубом или моделью, или нажмите кнопку с многоточием (**...**), чтобы вызвать диалоговое окно **Выбор удаленной папки** для выбора папки. Дополнительные сведения о диалоговом окне **Выбор удаленной папки** см. в разделе [Диалоговое окно "Выбор удаленной папки" (службы Analysis Services — многомерные данные)](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Дополнительные сведения о значениях этого свойства см. в разделе <xref:Microsoft.AnalysisServices.Cube.StorageLocation%2A>.|  
|**Состояние**|Отображает состояние обработки куба или модели. Дополнительные сведения о значениях этого свойства см. в разделе <xref:Microsoft.AnalysisServices.ProcessableMajorObject.State%2A>.|  
|**LastProcessed**|Отображает дату и время последней обработки куба или модели.|  
  
## <a name="see-also"></a>См. также:  
 [Analysis Services конструкторов и диалоговых окон &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Объекты куба &#40;Analysis Services многомерных данных&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
  
