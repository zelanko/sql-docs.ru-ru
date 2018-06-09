---
title: PredictAssociation (расширения интеллектуального анализа данных) | Документы Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7a23407b546bcde2dd1fde81654da4fe861e0719
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842977"
---
# <a name="predictassociation-dmx"></a>PredictAssociation (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Прогнозирует ассоциированное членство.  
  
Например функция PredictAssociation можно использовать для получения набора рекомендаций, учитывая его текущее состояние корзины покупок для клиента. 
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictAssociation(<table column reference>, option1, option2, n ...)  
```  
  
## <a name="applies-to"></a>Объект применения  
 Содержащие прогнозируемые вложенные таблицы, включая связи и некоторые алгоритмы классификации. Алгоритмы классификации, которые поддерживают вложенные таблицы: [!INCLUDE[msCoName](../includes/msconame-md.md)] дерева принятия решений, [!INCLUDE[msCoName](../includes/msconame-md.md)] упрощенного алгоритма Байеса и [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритмы нейронной сети.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 \<Таблица выражения >  
  
## <a name="remarks"></a>Примечания  
 Параметры для **PredictAssociation** функции включают EXCLUDE_NULL, INCLUDE_NULL, INCLUSIVE, EXCLUSIVE (по умолчанию), INPUT_ONLY, INCLUDE_STATISTICS и INCLUDE_NODE_ID.  
  
> [!NOTE]  
>  Параметры INCLUSIVE, EXCLUSIVE, INPUT_ONLY и INCLUDE_STATISTICS применяются только к ссылкам на столбцы таблицы, а EXCLUDE_NULL и INCLUDE_NULL — только к ссылкам на скалярные столбцы.  
  
 Возвращает только INCLUDE_STATISTICS **$Probability** и **$AdjustedProbability**.  
  
 Если задан числовой параметр *n* указано, **PredictAssociation** функция возвращает top n наиболее подходящих значений, на основе вероятности:  
  
```  
PredictAssociation(colref, [$AdjustedProbability], n)  
```  
  
 При включении **$AdjustedProbability**, инструкция возвращает верхние *n* значения в зависимости от **$AdjustedProbability**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется **PredictAssociation** функция, возвращающая четыре продуктов в Adventure Works базы данных, которые, скорее всего, будут проданы совместно.  
  
```  
SELECT  
  PredictAssociation([Association].[v Assoc Seq Line Items],4)  
From  
  [Association]  
```  
В следующем примере показано, как можно использовать вложенную таблицу в качестве входного для прогнозирующую функцию, с помощью предложения SHAPE. Запроса SHAPE создает набор строк с customerId как один столбец и вложенной таблицы в качестве второй столбец, который содержит список продуктов, которые у него клиент уже открыт. 

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
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; функции ссылки](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
