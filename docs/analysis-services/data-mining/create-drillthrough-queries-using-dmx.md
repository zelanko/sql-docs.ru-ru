---
title: "Создание запросов детализации с помощью расширений интеллектуального анализа данных | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42c896ee-e5ee-4017-b66e-31d1fe66d369
caps.latest.revision: 5
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 5
---
# Создание запросов детализации с помощью расширений интеллектуального анализа данных
  Для всех моделей с поддержкой детализации можно извлечь данные вариантов и структуры путем создания запроса DMX в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или любом другом клиенте с поддержкой DMX.  
  
> [!WARNING]  
>  Для просмотра нужных данных необходимо включить детализацию и иметь соответствующие разрешения.  
  
## Указание параметров детализации  
 Ниже приведен общий синтаксис для получения вариантов модели и структуры:  
  
```  
SELECT <model column list>, StructureColumn('<structure column name') FROM <modelname>.CASES  
```  
  
 Дополнительные сведения об использовании запросов DMX для возвращения данных по вариантам см. в разделах [SELECT FROM \<модель>.CASES (расширения интеллектуального анализа данных)](../Topic/SELECT%20FROM%20%3Cmodel%3E.CASES%20\(DMX\).md) и [SELECT FROM \<структура>.CASES](../Topic/SELECT%20FROM%20%3Cstructure%3E.CASES.md).  
  
## Примеры  
 Например, приведенный ниже DMX-запрос возвращает варианты для конкретной линейки продуктов в модели временных рядов. Этот запрос также возвращает столбец **Amount**, который не был использован в модели, но доступен в структуре интеллектуального анализа данных.  
  
```  
SELECT [DateSeries], [Model Region], Quantity, StructureColumn('Amount') AS [M200 Pacific Amount]  
FROM Forecasting.CASES  
WHERE [Model Region] = 'M200 Pacific'  
```  
  
 Обратите внимание, что в этом примере столбец структуры переименован с использованием псевдонима. Если столбцу структуры не присвоить псевдоним, то он будет возвращен с именем Expression. Это поведение по умолчанию для всех безымянных столбцов.  
  
## См. также  
 [Запросы детализации (интеллектуальный анализ данных)](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)   
 [Детализация структур интеллектуального анализа данных](../../analysis-services/data-mining/drillthrough-on-mining-structures.md)  
  
  