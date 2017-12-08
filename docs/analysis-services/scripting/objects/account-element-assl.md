---
title: "Учетная запись элемент (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Account Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Account
helpviewer_keywords: Account element
ms.assetid: 0bb7d06c-0158-4ab2-b2b1-cb50ba24f7c0
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: efe72ade8623910c34a1aff1d5439ee707c27f7b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="account-element-assl"></a>Элемент Account (ASSL)
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
|Количество элементов|0–n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Измерение счетов](../../../analysis-services/scripting/collections/accounts-element-assl.md)|  
|Дочерние элементы|[AccountType](../../../analysis-services/scripting/properties/accounttype-element-assl.md), [AggregationFunction](../../../analysis-services/scripting/properties/aggregationfunction-element-assl.md), [псевдонимы](../../../analysis-services/scripting/collections/aliases-element-assl.md), [заметок](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Измерения, которого [тип](../../../analysis-services/scripting/properties/type-element-dimension-assl.md) задан равным *учетные записи,* может иметь атрибут, который указывает тип учетной записи, например доходы или расходы и т. п., представляемый членами в измерении. Затем используется тип учетной записи [мер](../../../analysis-services/scripting/objects/measure-element-assl.md) элементов, которого [AggregationFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md) задан равным *ByAccount*, для определения статистической функции для использования при в статистической обработке элементов этого измерения. Элемент **Account** представляет один тип счета и статистическую функцию, которая должна использоваться такими мерами.  
  
 Тип учетной записи, которые должны быть перечислены, если Агрегатная функция отличается от используемого по умолчанию [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] для каждого типа счета.  
  
 Набор допустимых типов счетов фиксирован.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Database &#40; ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
