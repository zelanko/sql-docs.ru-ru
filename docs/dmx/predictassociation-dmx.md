---
title: PredictAssociation (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a834c87c3febf0554ad07334000d62f1f9a93fee
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86968260"
---
# <a name="predictassociation-dmx"></a>PredictAssociation (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Прогнозирует ассоциированное членство.  
  
Например, функцию PredictAssociation можно использовать для получения набора рекомендаций по текущему состоянию корзины покупок клиента. 
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictAssociation(<table column reference>, option1, option2, n ...)  
```  
  
## <a name="applies-to"></a>Применение  
 Алгоритмы, содержащие прогнозируемые вложенные таблицы, включая ассоциации и некоторые алгоритмы классификации. Алгоритмы классификации, поддерживающие вложенные таблицы, включают в себя [!INCLUDE[msCoName](../includes/msconame-md.md)] деревья принятия решений, [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритм Байеса (упрощенное и многоалгоритмное) [!INCLUDE[msCoName](../includes/msconame-md.md)] .  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 \<table expression>  
  
## <a name="remarks"></a>Комментарии  
 К параметрам функции **PredictAssociation** относятся EXCLUDE_NULL, INCLUDE_NULL, инклюзивные, монопольные (по умолчанию), INPUT_ONLY, INCLUDE_STATISTICS и INCLUDE_NODE_ID.  
  
> [!NOTE]  
>  Параметры INCLUSIVE, EXCLUSIVE, INPUT_ONLY и INCLUDE_STATISTICS применяются только к ссылкам на столбцы таблицы, а EXCLUDE_NULL и INCLUDE_NULL — только к ссылкам на скалярные столбцы.  
  
 INCLUDE_STATISTICS возвращает только **$Probability** и **$AdjustedProbability**.  
  
 Если указан числовой параметр *n* , функция **PredictAssociation** возвращает первые n наиболее вероятных значений в зависимости от вероятности:  
  
```  
PredictAssociation(colref, [$AdjustedProbability], n)  
```  
  
 При включении **$AdjustedProbability**инструкция возвращает первые *n* значений на основе **$AdjustedProbability**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере функция **PredictAssociation** используется для возврата четырех продуктов в базе данных Adventure Works, которые, скорее всего, будут продаваться вместе.  
  
```  
SELECT  
  PredictAssociation([Association].[v Assoc Seq Line Items],4)  
From  
  [Association]  
```  
В следующем примере показано, как можно использовать вложенную таблицу в качестве входных данных для функции прогнозирования с помощью предложения SHAPE. Запрос SHAPE создает набор строк с customerId как один столбец и вложенную таблицу в качестве второго столбца, содержащего список продуктов, которые уже были добавлены клиентом. 

~~~~
SELECT T.[CustomerId], PredictAssociation(MyNestedTable, 5) // returns top 5 associated items
FROM My Model
PREDICTION JOIN
SHAPE {
    OPENQUERY([Adventure Works DW],'SELECT CustomerID, OrderNumber
    FROM vAssocSeqOrders ORDER BY OrderNumber')
} APPEND (
    {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, model FROM 
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}
  RELATE OrderNumber to OrderNumber) AS T
~~~~  

  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/general-prediction-functions-dmx.md)  
  
  
