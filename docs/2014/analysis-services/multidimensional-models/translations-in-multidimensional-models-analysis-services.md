---
title: Переводы в многомерных моделях | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.deletelanguagefirm.f1
ms.assetid: 5521f8ef-b10a-4861-9df7-1e43e0a1fb3f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a80c7950ec4079021bbcf03d9ccee6970d68786b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66072734"
---
# <a name="translations-in-multidimensional-models"></a>Переводы в многомерных моделях
  Поддержка многоязычности в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] выполняется с помощью переводов. Перевод содержит код языка и привязки для свойств объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], которые могут быть представлены на различных языках. Например, можно задать перевод базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], чтобы представить заголовок и описание этой базы данных на некотором языке. Дополнительные сведения о переводах см. в разделе [переводы куба](../multidimensional-models-olap-logical-cube-objects/cube-translations.md).  
  
## <a name="defining-translations"></a>Определение переводов  
 Можно определить переводы в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , воспользовавшись соответствующим конструктором для объекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , который нужно перевести. При определении перевода создается объект `Translation`, связанный с соответствующим объектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и обладающий указанными явными символьными значениями (на выбранном языке) для свойств связанного объекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Следующие объекты и свойства в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] могут обладать связанными с ними переводами.  
  
|Объект|Свойства|Конструктор|  
|------------|----------------|--------------|  
|База данных|`Caption`, `Description`|[Общие &#40;конструктор баз данных&#41; &#40;Analysis Services многомерных данных&#41;](../general-database-designer-analysis-services-multidimensional-data.md)|  
|Cube|`Caption`, `Description`|[Переводы &#40;конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Группа мер|`Caption`|[Переводы &#40;конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Measure|`Caption`, `DisplayFolder`|[Переводы &#40;конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Измерение куба|`Caption`|[Переводы &#40;конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Перспектива|`Caption`|[Переводы &#40;конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Ключевой показатель эффективности|`Caption`, `Description`, `DisplayFolder`|[Переводы &#40;конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Действие|`Caption`|[Переводы &#40;конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Именованный набор|`Caption`|[Переводы &#40;конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Вычисляемый элемент|`Caption`|[Переводы &#40;конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Измерение базы данных|`Caption`, `AttributeAllMember`|[Переводы &#40;конструктор измерений&#41; &#40;Analysis Services многомерных данных&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
|attribute|`Caption`, `CaptionColumn` <sup>1</sup>, `AttributeHierarchyDisplayFolder`, `NamingTemplate`,`MembersWithDataCaption`|[Переводы &#40;конструктор измерений&#41; &#40;Analysis Services многомерных данных&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
|Иерархия|`Caption`, `AllMemberName`|[Переводы &#40;конструктор измерений&#41; &#40;Analysis Services многомерных данных&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
|Level|`Caption`|[Переводы &#40;конструктор измерений&#41; &#40;Analysis Services многомерных данных&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
  
 <sup>1</sup> `CaptionColumn` свойство атрибута может быть привязано к столбцу в представлении источника данных и может использовать параметры сортировки Windows, отличные от указанных для экземпляра, в отличие от других переводов.  
  
### <a name="defining-attribute-translations"></a>Задание переводов атрибутов  
 Переводы, связанные с атрибутами в измерениях базы данных, обрабатываются иначе, чем прочие переводы.  
  
-   Привязка столбца вместо явного символьного значения может быть связана со свойством `CaptionColumn`, так что имена элементов этого атрибута могут быть переведены.  
  
-   Можно использовать параметры сортировки Windows, отличные от параметров сортировки, заданного для экземпляра, так что элементы атрибута могут сортироваться способом, соответствующим языку, указанному в переводе.  
  
 Для определения переводов атрибутов в измерениях базы данных [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] можно использовать диалоговое окно **перевод данных атрибута** в. Дополнительные сведения о диалоговом окне **перевод данных атрибута** см. в разделе [диалоговое окно "перевод данных атрибута" &#40;Analysis Services многомерных данных&#41;](../attribute-data-translation-dialog-box-analysis-services-multidimensional-data.md).  
  
## <a name="resolving-translations"></a>Разрешение переводов  
 Если клиентское приложение запрашивает сведения по заданному идентификатору языка, экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] пытается разрешить данные и метаданные для объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в ближайший возможный идентификатор языка. Если клиентское приложение не задает язык по умолчанию или задает нейтральный код локали (0) или идентификатор языка процесса по умолчанию (1024), то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют язык по умолчанию для экземпляра, чтобы вернуть данные и метаданные для объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Если клиентское приложение задает идентификатор языка, отличный от идентификатора языка по умолчанию, экземпляр последовательно рассматривает все возможные переводы для всех возможных объектов. Если указанный идентификатор языка соответствует идентификатору языка перевода, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] возвращают этот перевод. Если соответствие не найдено, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] пытаются использовать один из следующих методов, чтобы вернуть переводы с идентификатором языка, ближайшим к указанному.  
  
-   Для следующих идентификаторов языка службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] пытаются использовать альтернативный идентификатор, если перевод для указанного идентификатора языка не определен.  
  
    |Заданный идентификатор языка|Альтернативный идентификатор языка|  
    |-----------------------------------|-----------------------------------|  
    |3076 — китайский (Гонконг, КНР)|1028 — китайский (Тайвань)|  
    |5124 — китайский (Макао)|1028 — китайский (Тайвань)|  
    |1028 — китайский (Тайвань)|Язык по умолчанию|  
    |4100 — китайский (Сингапур)|2052 — китайский (КНР)|  
    |2074 — хорватский|Язык по умолчанию|  
    |3098 — хорватский (кириллица)|Язык по умолчанию|  
  
-   Для всех остальных заданных идентификаторов языков службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] получают первичный язык по указанному идентификатору и возвращают идентификатор того языка, который Windows предлагает в качестве наилучшего совпадения с первичным. Язык по умолчанию используется, если для перевода не удается найти наиболее подходящий язык, а также, если указанный идентификатор языка наилучшим образом соответствует первичному языку.  
  
## <a name="deleting-translation-objects"></a>Удаление объектов перевода  
 Можно щелкнуть правой кнопкой мыши объект перевода в измерении или в конструкторе кубов, чтобы окончательно удалить его. Нельзя восстановить или повторно использовать удаленный объект, поэтому следует проверить список удаляемых объектов перед продолжением.  
  
## <a name="see-also"></a>См. также:  
 [Сценарии глобализации для Analysis Services многомерных](../globalization-scenarios-for-analysis-services-multiidimensional.md)   
 [Языки и параметры сортировки &#40;Analysis Services&#41;](../languages-and-collations-analysis-services.md)  
  
  
