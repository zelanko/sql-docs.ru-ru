---
title: Знакомство с измерениями (службы Analysis Services — многомерные данные) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 861e90f9ab453c1526089f4ad1b9c1ef16c989fb
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="dimensions---introduction"></a>Измерения — Введение
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Все Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] измерения — это группы атрибутов на основе столбцов из таблиц или представлений в представлении источника данных. Измерения существуют независимо от куба, могут использоваться в нескольких кубах или несколько раз в одном и том же кубе, а также могут быть связаны между экземплярами служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Измерение, существующее независимо от куба, называется измерением базы данных, а экземпляр измерения базы данных в кубе называется измерением куба.  
  
## <a name="dimension-based-on-a-star-schema-design"></a>Измерение, основанное на структуре схемы «звезда»  
 Структура измерения в основном определяется структурой таблицы или таблиц базового измерения. Простейшая структура называется схемой «звезда», в которой каждое измерение основано на одной таблице измерения, которая непосредственно связана с таблицей фактов связью первичного и внешнего ключей.  
  
 На следующей диаграмме показан подраздел [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] образца базы данных, в котором **FactResellerSales** таблица фактов связана с двумя таблицами измерений, **DimReseller** и **DimPromotion**. **ResellerKey** столбца в **FactResellerSales** таблицы фактов определяет связь внешнего ключа для **ResellerKey** столбец первичного ключа в  **DimReseller** таблицы измерения. Аналогичным образом **PromotionKey** столбца в **FactResellerSales** таблицы фактов определяет связь внешнего ключа для **PromotionKey** столбец первичного ключа в  **DimPromotion** таблицы измерения.  
  
 ![Логическая схема связи измерений фактов](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/media/dimfactrelationship.gif "логическая схема связи измерений фактов")  
  
## <a name="dimension-based-on-a-snowflake-schema-design"></a>Измерение, основанное на структуре схемы «снежинка»  
 Часто требуется более сложная структура, поскольку для определения измерения необходимы данные из нескольких таблиц. Эта схема называется схемой «снежинка», в которой каждое измерение основано на атрибутах из столбцов нескольких таблиц, связанных друг с другом и, в конечном итоге, с таблицей фактов связью первичного и внешнего ключей. Например, приведенной ниже диаграмме показаны таблицы, необходимые для полного описания измерения Product в **AdventureWorksDW** образец проекта:  
  
 ![Таблицы для измерения Product базы данных AdventureWorksAS](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/media/dimproduct.gif "таблицы для измерения Product базы данных AdventureWorksAS")  
  
 Чтобы полностью описать продукт, в измерение «Продукт» необходимо включить категорию и подкатегорию продукта. Тем не менее, эти сведения не содержатся непосредственно в главной таблицы для **DimProduct** измерения. Связь по внешнему ключу **DimProduct** для **DimProductSubcategory**, который в свою очередь имеет связь внешнего ключа для **DimProductCategory** таблицы, позволит можно включить данные о категориях и подкатегориях продуктов в измерении Product.  
  
## <a name="snowflake-schema-versus-reference-relationship"></a>Схема «снежинка» и ссылочная связь  
 В некоторых ситуациях возможен выбор между использованием схемы «снежинка» для определения атрибутов измерения из нескольких таблиц и определением двух отдельных измерений с последующим определением ссылочной связи измерений между ними. На следующей диаграмме показан этот сценарий.  
  
 ![Логическая схема образца ссылочное измерение](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/media/dimindirect.gif "логическая схема образца ссылочное измерение")  
  
 На предыдущей диаграмме **FactResellerSales** связь по внешнему ключу с таблицей фактов не имеет **DimGeography** таблицы измерения. Тем не менее **FactResellerSales** таблицы фактов имеют связь по внешнему ключу с **DimReseller** таблицы измерения, который в свою очередь имеет связь по внешнему ключу с  **DimGeography** таблицы измерения. Чтобы определить измерением посредника, содержащее географические данные обо всех посредниках, необходимо получить эти атрибуты из **DimGeography** и **DimReseller** таблиц измерений. Однако в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] аналогичный результат достигается путем создания двух отдельных измерений и связывания их в пределах группы мер путем определения ссылочной связи измерений между этими двумя измерениями. Дополнительные сведения о связях ссылочных измерений см. в разделе [связей измерений](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
 Одним из преимуществ последнего сценария является возможность создать одно измерение географии, а затем создать несколько измерений куба, основанных на этом измерении географии, без использования дополнительного пространства хранилища. Например, можно связать одно из измерений куба географии с измерением посредника, а другое измерение куба географии с измерением заказчика. **См. также:**[связей измерений](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), [определения ссылочной связи и свойств ссылочной связи](../../analysis-services/multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)  
  
## <a name="processing-a-dimension"></a>Обработка измерения  
 После создания измерения его необходимо обработать перед тем, как можно будет просматривать элементы атрибутов и иерархии в измерении. После изменения структуры измерения или обновления данных в его базовых таблицах измерение необходимо обработать еще раз перед тем, как можно будет просмотреть эти изменения. При обработке измерения после изменения структуры также необходимо обработать и все кубы, включающие это измерение. В противном случае куб будет недоступен для просмотра.  
  
## <a name="security"></a>безопасность  
 Безопасность всех элементов измерения, включая иерархии, уровни и элементы, обеспечивается с использованием ролей в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Безопасность измерения может быть применена ко всем кубам в базе данных, использующим это измерение, или к конкретному кубу. Дополнительные сведения о безопасности измерений см. в разделе [предоставить разрешения на измерении &#40;служб Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md).  
  
## <a name="see-also"></a>См. также  
 [Хранение измерений](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)   
 [Переводы измерений](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Измерения, доступные для записи](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
