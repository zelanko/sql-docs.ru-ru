---
title: Переводы в многомерных моделях | Документы Microsoft
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
- sql12.asvs.dimensiondesigner.deletelanguagefirm.f1
ms.assetid: 5521f8ef-b10a-4861-9df7-1e43e0a1fb3f
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: edb58addda246c716224b578aad3713812708476
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109598"
---
# <a name="translations-in-multidimensional-models"></a>Переводы в многомерных моделях
  Поддержка различных языков в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] осуществляется с помощью переводов. Перевод содержит код языка и привязки для свойств объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], которые могут быть представлены на различных языках. Например, можно задать перевод базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], чтобы представить заголовок и описание этой базы данных на некотором языке. Дополнительные сведения о переводах см. в разделе [Переводы куба](../multidimensional-models-olap-logical-cube-objects/cube-translations.md).  
  
## <a name="defining-translations"></a>Определение переводов  
 Можно определить переводы в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , воспользовавшись соответствующим конструктором для объекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , который нужно перевести. При определении перевода создается `Translation` объект, связанный с соответствующим [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объект с указанными явными символьными значениями на определенном языке, для свойств связанного [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объекта.  
  
 Следующие объекты и свойства в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] могут обладать связанными с ними переводами.  
  
|Объект|Свойства|Конструктор|  
|------------|----------------|--------------|  
|База данных|`Caption`, `Description`|[Общие &#40;базы данных конструктор&#41; &#40;службы Analysis Services — многомерные данные&#41;](../general-database-designer-analysis-services-multidimensional-data.md)|  
|Cube|`Caption`, `Description`|[Переводы &#40;конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Группа мер|`Caption`|[Переводы &#40;конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Measure|`Caption`, `DisplayFolder`|[Переводы &#40;конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Измерение куба|`Caption`|[Переводы &#40;конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Перспектива|`Caption`|[Переводы &#40;конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Ключевой показатель эффективности|`Caption`, `Description`, `DisplayFolder`|[Переводы &#40;конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Действие|`Caption`|[Переводы &#40;конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Именованный набор|`Caption`|[Переводы &#40;конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|вычисляемый элемент|`Caption`|[Переводы &#40;конструктор кубов&#41; &#40;службы Analysis Services — многомерные данные&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Измерение базы данных|`Caption`, `AttributeAllMember`|[Переводы &#40;конструктор измерений&#41; &#40;службы Analysis Services — многомерные данные&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
|attribute|`Caption`, `CaptionColumn` <sup>1</sup>, `AttributeHierarchyDisplayFolder`, `NamingTemplate`, `MembersWithDataCaption`|[Переводы &#40;конструктор измерений&#41; &#40;службы Analysis Services — многомерные данные&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
|Иерархия|`Caption`, `AllMemberName`|[Переводы &#40;конструктор измерений&#41; &#40;службы Analysis Services — многомерные данные&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
|Level|`Caption`|[Переводы &#40;конструктор измерений&#41; &#40;службы Analysis Services — многомерные данные&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
  
 <sup>1</sup> `CaptionColumn` свойства атрибута может быть привязано к столбцу в представлении источника данных и можно использовать параметры сортировки Windows, отличный от того, указанный для экземпляра, в противоположность другим переводам.  
  
### <a name="defining-attribute-translations"></a>Задание переводов атрибутов  
 Переводы, связанные с атрибутами в измерениях базы данных, обрабатываются иначе, чем прочие переводы.  
  
-   Привязка столбца вместо явного символьного значения может быть связана со свойством `CaptionColumn`, так что имена элементов этого атрибута могут быть переведены.  
  
-   Можно использовать параметры сортировки Windows, отличные от параметров сортировки, заданного для экземпляра, так что элементы атрибута могут сортироваться способом, соответствующим языку, указанному в переводе.  
  
 Можно использовать **перевод данных атрибута** диалоговое окно в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] чтобы определить переводы для атрибутов в измерениях базы данных. Дополнительные сведения о **перевод данных атрибута** диалоговое окно, в разделе [диалогового перевод данных атрибута &#40;службы Analysis Services — многомерные данные&#41;](../attribute-data-translation-dialog-box-analysis-services-multidimensional-data.md).  
  
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
  
## <a name="see-also"></a>См. также  
 [Сценарии глобализации для многомерных служб Analysis Services](../globalization-scenarios-for-analysis-services-multiidimensional.md)   
 [Языки и параметры сортировки &#40;служб Analysis Services&#41;](../languages-and-collations-analysis-services.md)  
  
  