---
title: Учетная запись элемент (ASSL) | Документация Майкрософт
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d763b75cfb357554948565a59f5348d7fd3b725a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321176"
---
# <a name="account-element-assl"></a>Элемент Account (ASSL)
  Содержит сведения о типе счета в [базы данных](database-element-assl.md) элемент.  
  
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
 Измерения, которого [тип](../properties/type-element-dimension-assl.md) элементу присваивается *учетные записи,* может иметь атрибут, определяющий тип учетной записи, например доходы или расходы и т. п., представляемый членами в измерении. Затем тип счета используется элементами [мер](measure-element-assl.md) элементы, которых [AggregationFunction](../properties/aggregatefunction-element-assl.md) элементу присваивается *ByAccount*, для определения статистической функции, которые используются, когда в статистической обработке элементов этого измерения. Элемент `Account` представляет один тип счета и статистическую функцию, которая должна использоваться такими мерами.  
  
 Тип учетной записи должна быть указана, если Агрегатная функция отличается от используемого по умолчанию [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] для каждого типа счета.  
  
 Набор допустимых типов счетов фиксирован.  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Database описания &#40;ASSL&#41;](database-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
