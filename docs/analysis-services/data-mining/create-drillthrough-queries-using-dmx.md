---
title: Создание запросов детализации с помощью расширений интеллектуального анализа данных | Документы Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0a16e2cd247a312778a7c90b214379dad736cf8d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
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
  
  
