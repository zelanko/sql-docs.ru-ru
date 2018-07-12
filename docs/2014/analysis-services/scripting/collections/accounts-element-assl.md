---
title: Учетные записи элемент (ASSL) | Документация Майкрософт
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
- Accounts Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Accounts
helpviewer_keywords:
- Accounts element
ms.assetid: 3ec62f58-c19b-4b15-b040-8941521a389b
caps.latest.revision: 44
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 94e167c6eb804f3372fab6974403f0303f21a13a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37277970"
---
# <a name="accounts-element-assl"></a>Элемент Accounts (ASSL)
  Содержит коллекцию типов учетных записей, которые определены в [базы данных](../objects/database-element-assl.md) элемент.  
  
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[База данных](../objects/database-element-assl.md)|  
|Дочерние элементы|[Учетная запись](../objects/account-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Измерения, которого [тип](../properties/type-element-dimension-assl.md) элементу присваивается *учетные записи*, могут иметь атрибут, указывающий тип учетной записи, например доходы или расходы и так далее, представленный членами в измерении. Затем тип счета используется элементами [мер](../objects/measure-element-assl.md) элементы, которых [AggregationFunction](../properties/aggregatefunction-element-assl.md) элементу присваивается *ByAccount*, для определения статистической функции, которые используются, когда в статистической обработке элементов этого измерения. Элемент `Accounts` хранит коллекцию элементов `Account`, которые представляют типы счетов и статистическую функцию, предназначенную для использования с каждым типом счета.  
  
 Тип учетной записи должна быть указана, если Агрегатная функция отличается от используемого по умолчанию [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] для каждого типа счета.  
  
 Набор допустимых типов счетов фиксирован.  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.AccountCollection>.  
  
## <a name="see-also"></a>См. также  
 [Элемент AccountType &#40;ASSL&#41;](../properties/accounttype-element-assl.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
