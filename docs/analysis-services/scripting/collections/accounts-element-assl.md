---
title: "Учетные записи элемент (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Accounts Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Accounts
helpviewer_keywords:
- Accounts element
ms.assetid: 3ec62f58-c19b-4b15-b040-8941521a389b
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3d781e32f57f9df9cc5bf180e37761c8a26c0848
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="accounts-element-assl"></a>Элемент Accounts (ASSL)
  Содержит коллекцию типов учетных записей, которые определены в [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Database>  
   ...  
   <Accounts>  
      <Account>...</Account>  
   </Accounts>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|нет (коллекция)|  
|Значение по умолчанию|нет (коллекция)|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[База данных](../../../analysis-services/scripting/objects/database-element-assl.md)|  
|Дочерние элементы|[Учетная запись](../../../analysis-services/scripting/objects/account-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Измерения, которого [тип](../../../analysis-services/scripting/properties/type-element-dimension-assl.md) задан равным *учетные записи*, могут иметь атрибут, определяющий тип учетной записи, например доходы или расходы и так далее, представленный членами в измерении. Затем используется тип учетной записи [мер](../../../analysis-services/scripting/objects/measure-element-assl.md) элементов, которого [AggregationFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md) задан равным *ByAccount*, для определения статистической функции для использования при в статистической обработке элементов этого измерения. Элемент **Accounts** хранит коллекцию элементов **Account** , которые представляют типы счетов и статистическую функцию, предназначенную для использования с каждым типом счета.  
  
 Тип учетной записи, которые должны быть перечислены, если Агрегатная функция отличается от используемого по умолчанию [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] для каждого типа счета.  
  
 Набор допустимых типов счетов фиксирован.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AccountCollection>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент AccountType &#40; ASSL &#41;](../../../analysis-services/scripting/properties/accounttype-element-assl.md)   
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

