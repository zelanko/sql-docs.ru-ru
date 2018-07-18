---
title: Введение в измерения (службы Analysis Services — многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], about dimensions
- storage [Analysis Services], dimensions
- dimensions [Analysis Services], examples
- storing data [Analysis Services], dimensions
- storage [Analysis Services]
ms.assetid: ab170fdd-4144-42db-9497-690b9189fc25
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 662e7d0402a26b2c6c71e3717673a3f7340dd34c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247614"
---
# <a name="introduction-to-dimensions-analysis-services---multidimensional-data"></a>Введение в измерения (службы Analysis Services — многомерные данные)
  Все Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] измерения — это группы атрибутов на основе столбцов из таблиц или представлений в представлении источника данных. Измерения существуют независимо от куба, могут использоваться в нескольких кубах или несколько раз в одном и том же кубе, а также могут быть связаны между экземплярами служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Измерение, существующее независимо от куба, называется измерением базы данных, а экземпляр измерения базы данных в кубе называется измерением куба.  
  
## <a name="dimension-based-on-a-star-schema-design"></a>Измерение, основанное на структуре схемы «звезда»  
 Структура измерения в основном определяется структурой таблицы или таблиц базового измерения. Простейшая структура называется схемой «звезда», в которой каждое измерение основано на одной таблице измерения, которая непосредственно связана с таблицей фактов связью первичного и внешнего ключей.  
  
 На следующей схеме показана часть [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] образца базы данных, в котором **FactResellerSales** таблица фактов связана с двумя таблицами измерений, **DimReseller** и **DimPromotion**. **ResellerKey** столбца в **FactResellerSales** таблицы фактов определяет связи по внешнему ключу для **ResellerKey** столбец первичного ключа в  **DimReseller** таблицы измерения. Аналогичным образом **PromotionKey** столбца в **FactResellerSales** таблицы фактов определяет связи по внешнему ключу для **PromotionKey** столбец первичного ключа в  **DimPromotion** таблицы измерения.  
  
 ![Логическая схема связи измерений фактов](../../../2014/analysis-services/dev-guide/media/dimfactrelationship.gif "логическая схема связи измерений фактов")  
  
## <a name="dimension-based-on-a-snowflake-schema-design"></a>Измерение, основанное на структуре схемы «снежинка»  
 Часто требуется более сложная структура, поскольку для определения измерения необходимы данные из нескольких таблиц. Эта схема называется схемой «снежинка», в которой каждое измерение основано на атрибутах из столбцов нескольких таблиц, связанных друг с другом и, в конечном итоге, с таблицей фактов связью первичного и внешнего ключей. Например, на схеме ниже таблицы, необходимые для полного описания измерения Product в **AdventureWorksDW** пример проекта:  
  
 ![Таблицы для измерения Product базы данных AdventureWorksAS](../../../2014/analysis-services/dev-guide/media/dimproduct.gif "таблицы для измерения Product базы данных AdventureWorksAS")  
  
 Чтобы полностью описать продукт, в измерение «Продукт» необходимо включить категорию и подкатегорию продукта. Тем не менее, эти сведения не содержатся непосредственно в главную таблицу для **DimProduct** измерения. Связи по внешнему ключу из **DimProduct** для **DimProductSubcategory**, который в свою очередь имеет связи по внешнему ключу для **DimProductCategory** таблицы, позволит Возможно, чтобы включить данные о категориях и подкатегориях продуктов в измерении Product.  
  
## <a name="snowflake-schema-versus-reference-relationship"></a>Схема «снежинка» и ссылочная связь  
 В некоторых ситуациях возможен выбор между использованием схемы «снежинка» для определения атрибутов измерения из нескольких таблиц и определением двух отдельных измерений с последующим определением ссылочной связи измерений между ними. На следующей диаграмме показан этот сценарий.  
  
 ![Логическая схема образца ссылочное измерение](../../../2014/analysis-services/dev-guide/media/dimindirect.gif "логическая схема образца ссылочного измерения")  
  
 На предыдущей диаграмме **FactResellerSales** таблица фактов не имеет связи по внешнему ключу с **DimGeography** таблицы измерения. Тем не менее **FactResellerSales** таблицы фактов имеют связь по внешнему ключу с **DimReseller** таблица измерения, который в свою очередь имеет связь по внешнему ключу с  **DimGeography** таблицы измерения. Чтобы определить измерение «посредник», содержащее географические данные обо всех посредниках, необходимо получить эти атрибуты из **DimGeography** и **DimReseller** таблиц измерений. Однако в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] аналогичный результат достигается путем создания двух отдельных измерений и связывания их в пределах группы мер путем определения ссылочной связи измерений между этими двумя измерениями. Дополнительные сведения о связях ссылочных измерений см. в разделе [связей измерений](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
 Одним из преимуществ последнего сценария является возможность создать одно измерение географии, а затем создать несколько измерений куба, основанных на этом измерении географии, без использования дополнительного пространства хранилища. Например, можно связать одно из измерений куба географии с измерением посредника, а другое измерение куба географии с измерением заказчика. **См. также:**[связей измерений](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), [Определение ссылочной связи и свойств ссылочной связи](../multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)  
  
## <a name="processing-a-dimension"></a>Обработка измерения  
 После создания измерения его необходимо обработать перед тем, как можно будет просматривать элементы атрибутов и иерархии в измерении. После изменения структуры измерения или обновления данных в его базовых таблицах измерение необходимо обработать еще раз перед тем, как можно будет просмотреть эти изменения. При обработке измерения после изменения структуры также необходимо обработать и все кубы, включающие это измерение. В противном случае куб будет недоступен для просмотра.  
  
## <a name="security"></a>безопасность  
 Безопасность всех элементов измерения, включая иерархии, уровни и элементы, обеспечивается с использованием ролей в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Безопасность измерения может быть применена ко всем кубам в базе данных, использующим это измерение, или к конкретному кубу. Дополнительные сведения о безопасности измерений см. в разделе [предоставить разрешения на измерение &#40;служб Analysis Services&#41;](../multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md).  
  
## <a name="see-also"></a>См. также  
 [Хранение измерений](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)   
 [Переводы измерений](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Измерения, доступные для записи](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
