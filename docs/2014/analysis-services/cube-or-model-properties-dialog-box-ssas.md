---
title: Куб или модель диалоговое окно «Свойства» (службы SSAS) | Документация Майкрософт
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66086601"
---
# <a name="cube-or-model-properties-dialog-box-ssas"></a>Диалоговое окно «Свойства куба или модели» (SSAS)
  Используйте диалоговое окно **Свойства базы данных** в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] для установки свойств куба или шаблона базы данных. Чтобы вызвать это диалоговое окно, необходимо щелкнуть правой клавишей мыши куб или модель в **обозревателе объектов** и выбрать пункт **Свойства**.  
  
 Это диалоговое окно также содержит вкладки для следующих свойств:  
  
-   [Редактор форм действий отчетов &#40;вкладка «действия», конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
-   [Конфигурация ошибок при обработке измерения кубов, секции и &#40;службы SSAS — многомерные&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)  
  
-   [Упреждающее кэширование &#40;секционировать диалоговое окно свойств&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md)  
  
## <a name="options"></a>Параметры  
  
|Термин|Определение|  
|----------|----------------|  
|**Name**|Отображает имя куба или модели.|  
|**Идентификатор**|Отображает идентификатор куба или модели.|  
|**Описание**|Отображает описание куба или модели.|  
|**Отметка времени создания**|Отображает дату и время создания куба или модели.|  
|**Последнее обновление схемы**|Отображает дату и время последнего обновления метаданных куба или модели.|  
|**Режим обработки кэша скриптов**|Выберите режим обработки, который следует использовать для кэша скриптов куба или модели. Дополнительные сведения о значениях этого свойства см. в разделе <xref:Microsoft.AnalysisServices.Cube.ScriptCacheProcessingMode%2A>.|  
|**Режим обработки**|Выберите режим обработки для указанного куба или модели. Дополнительные сведения о значениях этого свойства см. в разделе <xref:Microsoft.AnalysisServices.Cube.ProcessingMode%2A>.|  
|**Место хранения**|Введите имя папки, которая будет использоваться по умолчанию как место хранения для групп мер и секций, связанных с кубом или моделью, или нажмите кнопку с многоточием ( **...** ), чтобы вызвать диалоговое окно **Выбор удаленной папки** для выбора папки. Дополнительные сведения о диалоговом окне **Выбор удаленной папки** см. в разделе [Диалоговое окно "Выбор удаленной папки" (службы Analysis Services — многомерные данные)](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Дополнительные сведения о значениях этого свойства см. в разделе <xref:Microsoft.AnalysisServices.Cube.StorageLocation%2A>.|  
|**Состояние**|Отображает состояние обработки куба или модели. Дополнительные сведения о значениях этого свойства см. в разделе <xref:Microsoft.AnalysisServices.ProcessableMajorObject.State%2A>.|  
|**LastProcessed**|Отображает дату и время последней обработки куба или модели.|  
  
## <a name="see-also"></a>См. также  
 [Конструкторы и диалоговые окна служб Analysis Services &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Объекты куба &#40;службы Analysis Services — многомерные данные&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
  
