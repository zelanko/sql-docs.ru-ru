---
title: Учетная запись элемент (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Account Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Account
helpviewer_keywords:
- Account element
ms.assetid: 0bb7d06c-0158-4ab2-b2b1-cb50ba24f7c0
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0a99dbaee6e1eaec95385295cf1842ffcc336adf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194127"
---
# <a name="account-element-assl"></a>Элемент Account (ASSL)
  Содержит сведения о типе счета в [базы данных](database-element-assl.md) элемента.  
  
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
|Родительские элементы|[Измерение счетов](../collections/accounts-element-assl.md)|  
|Дочерние элементы|[AccountType](../properties/accounttype-element-assl.md), [AggregationFunction](../properties/aggregationfunction-element-assl.md), [псевдонимы](../collections/aliases-element-assl.md), [заметок](../collections/annotations-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Измерения, которого [тип](../properties/type-element-dimension-assl.md) задан равным *учетные записи,* может иметь атрибут, который указывает тип учетной записи, например доходы или расходы и т. п., представляемый членами в измерении. Затем используется тип учетной записи [мер](measure-element-assl.md) элементов, которого [AggregationFunction](../properties/aggregatefunction-element-assl.md) задан равным *ByAccount*, для определения статистической функции для использования при в статистической обработке элементов этого измерения. Элемент `Account` представляет один тип счета и статистическую функцию, которая должна использоваться такими мерами.  
  
 Тип учетной записи, которые должны быть перечислены, если Агрегатная функция отличается от используемого по умолчанию [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] для каждого типа счета.  
  
 Набор допустимых типов счетов фиксирован.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Database &#40;ASSL&#41;](database-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  