---
title: Учетные записи элемент (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bf3d3b56e9cc2b299ddcdec1c0a506e0168f8741
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="accounts-element-assl"></a>Элемент Accounts (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
## <a name="remarks"></a>Примечания  
 Измерения, которого [тип](../../../analysis-services/scripting/properties/type-element-dimension-assl.md) задан равным *учетные записи*, могут иметь атрибут, определяющий тип учетной записи, например доходы или расходы и так далее, представленный членами в измерении. Затем используется тип учетной записи [мер](../../../analysis-services/scripting/objects/measure-element-assl.md) элементов, которого [AggregationFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md) задан равным *ByAccount*, для определения статистической функции для использования при в статистической обработке элементов этого измерения. Элемент **Accounts** хранит коллекцию элементов **Account** , которые представляют типы счетов и статистическую функцию, предназначенную для использования с каждым типом счета.  
  
 Тип учетной записи, которые должны быть перечислены, если Агрегатная функция отличается от используемого по умолчанию [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] для каждого типа счета.  
  
 Набор допустимых типов счетов фиксирован.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AccountCollection>.  
  
## <a name="see-also"></a>См. также  
 [Элемент AccountType &#40;ASSL&#41;](../../../analysis-services/scripting/properties/accounttype-element-assl.md)   
 [Коллекции & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
