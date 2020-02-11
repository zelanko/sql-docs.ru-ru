---
title: Общие сведения об измерениях (Analysis Services-многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], about dimensions
- storage [Analysis Services], dimensions
- dimensions [Analysis Services], examples
- storing data [Analysis Services], dimensions
- storage [Analysis Services]
ms.assetid: ab170fdd-4144-42db-9497-690b9189fc25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2dce25d6638c5ec921ec22601ed73d03a2ccb215
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68887862"
---
# <a name="introduction-to-dimensions-analysis-services---multidimensional-data"></a>Введение в измерения (службы Analysis Services — многомерные данные)
  Все измерения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Майкрософт — это группы атрибутов, основанные на столбцах таблиц или представлений в представлении источника данных. Измерения существуют независимо от куба, могут использоваться в нескольких кубах или несколько раз в одном и том же кубе, а также могут быть связаны между экземплярами служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Измерение, существующее независимо от куба, называется измерением базы данных, а экземпляр измерения базы данных в кубе называется измерением куба.  
  
## <a name="dimension-based-on-a-star-schema-design"></a>Измерение, основанное на структуре схемы «звезда»  
 Структура измерения в основном определяется структурой таблицы или таблиц базового измерения. Простейшая структура называется схемой «звезда», в которой каждое измерение основано на одной таблице измерения, которая непосредственно связана с таблицей фактов связью первичного и внешнего ключей.  
  
 На следующей схеме показан [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] подраздел базы данных, в котором таблица фактов **FactResellerSales** связана с двумя таблицами измерений, **DimReseller** и **DimPromotion**. Столбец **ResellerKey** в таблице фактов **FactResellerSales** определяет связь по внешнему ключу с первичным ключевым столбцом **ResellerKey** в таблице измерения **DimReseller** . Аналогичным образом столбец **промотионкэй** в таблице фактов **FactResellerSales** определяет связь по внешнему ключу с первичным ключевым столбцом **промотионкэй** в таблице измерения **DimPromotion** .  
  
 ![Логическая схема связи измерений фактов](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/dimfactrelationship.gif "Логическая схема связи измерений фактов")  
  
## <a name="dimension-based-on-a-snowflake-schema-design"></a>Измерение, основанное на структуре схемы «снежинка»  
 Часто требуется более сложная структура, поскольку для определения измерения необходимы данные из нескольких таблиц. Эта схема называется схемой «снежинка», в которой каждое измерение основано на атрибутах из столбцов нескольких таблиц, связанных друг с другом и, в конечном итоге, с таблицей фактов связью первичного и внешнего ключей. Например, на следующей схеме показаны таблицы, необходимые для полного описания измерения Product в образце проекта **AdventureWorksDW** .  
  
 ![Таблицы измерения Product базы данных AdventureWorksAS](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/dimproduct.gif "Таблицы измерения Product базы данных AdventureWorksAS")  
  
 Чтобы полностью описать продукт, в измерение «Продукт» необходимо включить категорию и подкатегорию продукта. Однако эта информация не находится непосредственно в основной таблице для измерения **DimProduct** . Связь по внешнему ключу от **DimProduct** к **DimProductSubcategory**, которая, в свою очередь, имеет связь по внешнему ключу с таблицей **DimProductCategory** , позволяет включать сведения о категориях продуктов и подкатегориях в измерении Product.  
  
## <a name="snowflake-schema-versus-reference-relationship"></a>Схема «снежинка» и ссылочная связь  
 В некоторых ситуациях возможен выбор между использованием схемы «снежинка» для определения атрибутов измерения из нескольких таблиц и определением двух отдельных измерений с последующим определением ссылочной связи измерений между ними. На следующей диаграмме показан этот сценарий.  
  
 ![Логическая схема образца измерения, на который дана ссылка](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/dimindirect.gif "Логическая схема образца измерения, на который дана ссылка")  
  
 На предыдущей схеме таблица фактов **FactResellerSales** не имеет связи внешнего ключа с таблицей измерения **DimGeography** . Однако таблица фактов **FactResellerSales** имеет связь по внешнему ключу с таблицей измерения **DimReseller** , которая, в свою очередь, имеет связь по внешнему ключу с таблицей измерения **DimGeography** . Чтобы определить измерение торгового посредника, содержащее географические сведения о каждом торговом посреднике, необходимо извлечь эти атрибуты из таблиц измерений **DimGeography** и **DimReseller** . Однако в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] аналогичный результат достигается путем создания двух отдельных измерений и связывания их в пределах группы мер путем определения ссылочной связи измерений между этими двумя измерениями. Дополнительные сведения о связях ссылочных измерений см. в разделе [связи измерений](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
 Одним из преимуществ последнего сценария является возможность создать одно измерение географии, а затем создать несколько измерений куба, основанных на этом измерении географии, без использования дополнительного пространства хранилища. Например, можно связать одно из измерений куба географии с измерением посредника, а другое измерение куба географии с измерением заказчика. **См. также:**[связи измерений](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), [Определение ссылочной связи и свойств ссылочной связи](../multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)  
  
## <a name="processing-a-dimension"></a>Обработка измерения  
 После создания измерения его необходимо обработать перед тем, как можно будет просматривать элементы атрибутов и иерархии в измерении. После изменения структуры измерения или обновления данных в его базовых таблицах измерение необходимо обработать еще раз перед тем, как можно будет просмотреть эти изменения. При обработке измерения после изменения структуры также необходимо обработать и все кубы, включающие это измерение. В противном случае куб будет недоступен для просмотра.  
  
## <a name="security"></a>безопасность  
 Безопасность всех элементов измерения, включая иерархии, уровни и элементы, обеспечивается с использованием ролей в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Безопасность измерения может быть применена ко всем кубам в базе данных, использующим это измерение, или к конкретному кубу. Дополнительные сведения о безопасности измерений см. в разделе [предоставление разрешений на измерение &#40;Analysis Services&#41;](../multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Хранилище измерений](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)   
 [Переводы измерений](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Измерения, доступные для записи](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
