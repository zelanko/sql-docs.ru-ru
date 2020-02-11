---
title: PredictAssociation (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ea0a9915e062d7b6f15b63e18976e88cc339202d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "76939498"
---
# <a name="predictassociation-dmx"></a>PredictAssociation (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Прогнозирует ассоциированное членство.  
  
Например, функцию PredictAssociation можно использовать для получения набора рекомендаций по текущему состоянию корзины покупок клиента. 
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictAssociation(<table column reference>, option1, option2, n ...)  
```  
  
## <a name="applies-to"></a>Применяется к  
 Алгоритмы, содержащие прогнозируемые вложенные таблицы, включая ассоциации и некоторые алгоритмы классификации. Алгоритмы классификации, поддерживающие вложенные [!INCLUDE[msCoName](../includes/msconame-md.md)] таблицы, включают [!INCLUDE[msCoName](../includes/msconame-md.md)] в себя деревья принятия [!INCLUDE[msCoName](../includes/msconame-md.md)] решений, алгоритм Байеса (упрощенное и многоалгоритмное).  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 \<табличное выражение>  
  
## <a name="remarks"></a>Remarks  
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

  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/general-prediction-functions-dmx.md)  
  
  
