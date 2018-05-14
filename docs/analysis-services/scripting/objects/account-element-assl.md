---
title: Учетная запись элемент (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0e9cda9f82df4f1b7a6d445d7cb85e69c635833f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="account-element-assl"></a>Элемент Account (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит сведения о типе счета в [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Accounts>  
   <Account>  
      <AccountType>...</AccountType>  
      <AggregationFunction>...</AggregationFunction>  
            <Aliases>...</Aliases>  
            <Annotations>...</Annotations>  
   </Account>  
</Accounts>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Измерение счетов](../../../analysis-services/scripting/collections/accounts-element-assl.md)|  
|Дочерние элементы|[AccountType](../../../analysis-services/scripting/properties/accounttype-element-assl.md), [AggregationFunction](../../../analysis-services/scripting/properties/aggregationfunction-element-assl.md), [псевдонимы](../../../analysis-services/scripting/collections/aliases-element-assl.md), [заметок](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Измерения, которого [тип](../../../analysis-services/scripting/properties/type-element-dimension-assl.md) задан равным *учетные записи,* может иметь атрибут, который указывает тип учетной записи, например доходы или расходы и т. п., представляемый членами в измерении. Затем используется тип учетной записи [мер](../../../analysis-services/scripting/objects/measure-element-assl.md) элементов, которого [AggregationFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md) задан равным *ByAccount*, для определения статистической функции для использования при в статистической обработке элементов этого измерения. Элемент **Account** представляет один тип счета и статистическую функцию, которая должна использоваться такими мерами.  
  
 Тип учетной записи, которые должны быть перечислены, если Агрегатная функция отличается от используемого по умолчанию [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] для каждого типа счета.  
  
 Набор допустимых типов счетов фиксирован.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Database &#40;ASSL&#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
