---
title: "Создание запросов детализации с помощью расширений интеллектуального анализа данных | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c896ee-e5ee-4017-b66e-31d1fe66d369
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dda090411aae5baf577c49e76176eab2835c1df9
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="create-drillthrough-queries-using-dmx"></a>Создание запросов детализации с помощью расширений интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Для всех моделей с поддержкой детализации можно извлечь данные вариантов и структуры путем создания запроса DMX в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или любом другом клиенте с поддержкой DMX.  
  
> [!WARNING]  
>  Для просмотра нужных данных необходимо включить детализацию и иметь соответствующие разрешения.  
  
## <a name="specifying-drillthrough-options"></a>Указание параметров детализации  
 Ниже приведен общий синтаксис для получения вариантов модели и структуры:  
  
```  
SELECT <model column list>, StructureColumn('<structure column name') FROM <modelname>.CASES  
```  
  
 Дополнительные сведения об использовании запросов DMX для возвращения данных по вариантам см. в разделах [SELECT FROM &#60;модель&#62;.CASES &#40;расширения интеллектуального анализа данных&#41;](../../dmx/select-from-model-cases-dmx.md) и [SELECT FROM &#60;структура&#62;.CASES](../../dmx/select-from-structure-cases.md).  
  
## <a name="examples"></a>Примеры  
 Например, приведенный ниже DMX-запрос возвращает варианты для конкретной линейки продуктов в модели временных рядов. Этот запрос также возвращает столбец **Amount**, который не был использован в модели, но доступен в структуре интеллектуального анализа данных.  
  
```  
SELECT [DateSeries], [Model Region], Quantity, StructureColumn('Amount') AS [M200 Pacific Amount]  
FROM Forecasting.CASES  
WHERE [Model Region] = 'M200 Pacific'  
```  
  
 Обратите внимание, что в этом примере столбец структуры переименован с использованием псевдонима. Если столбцу структуры не присвоить псевдоним, то он будет возвращен с именем Expression. Это поведение по умолчанию для всех безымянных столбцов.  
  
## <a name="see-also"></a>См. также  
 [Запросы детализации &#40; интеллектуального анализа данных и &#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)   
 [Детализация структур интеллектуального анализа данных](../../analysis-services/data-mining/drillthrough-on-mining-structures.md)  
  
  
