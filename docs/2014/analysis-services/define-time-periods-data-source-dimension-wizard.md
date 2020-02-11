---
title: Определение временных периодов (источник данных) (мастер измерений) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.timeperioddefinition.f1
ms.assetid: a5e6b9ff-69fa-4896-a840-de2b3e063ca9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 23e40c9500a2d8c571e10fdddb09f2de289cd714
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66082010"
---
# <a name="define-time-periods-data-source-dimension-wizard"></a>Определение временных периодов (источник данных) (мастер измерений)
  Страница **Определение временных периодов** используется для определения атрибутов, представляющих периоды времени в измерении времени, которое имеет столбцы в таблице, заданной на странице **Выбор типа измерения** .  
  
> [!NOTE]  
>  Эта страница отображается только в том случае, если выбран параметр **Построение измерения с использованием источника данных** на странице **Определение измерения** и **Измерение времени** на странице **Выбор типа измерения** .  
  
## <a name="options"></a>Параметры  
 **Имя свойства времени**  
 Выводит типы атрибутов, которые используются для указания периодов времени в измерении времени. Дополнительные сведения о типах атрибутов см. в разделе [Элемент Type (DimensionAttribute) (ASSL)](https://docs.microsoft.com/bi-reference/assl/properties/type-element-dimensionattribute-assl).  
  
> [!NOTE]  
>  Тип атрибута `Date` должен использоваться только для столбцов с типом данных DateTime.  
  
 **Столбцы таблицы времени**  
 Перечисляет столбцы, на которых будут построены соответствующие типы атрибутов.  
  
 Чтобы изменить этот столбец, щелкните его, а затем выберите в списке другой столбец.  
  
## <a name="see-also"></a>См. также:  
 [Справка F1 мастера измерений](dimension-wizard-f1-help.md)   
 [Измерения &#40;Analysis Services многомерных данных&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Измерения в многомерных моделях](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
