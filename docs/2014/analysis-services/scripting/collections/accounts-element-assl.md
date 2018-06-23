---
title: Учетные записи элемент (ASSL) | Документы Microsoft
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 30fcd1815ac785ab71c90a935b9392ab5e85e98b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086999"
---
# <a name="accounts-element-assl"></a>Элемент Accounts (ASSL)
  Содержит коллекцию типов учетных записей, которые определены в [базы данных](../objects/database-element-assl.md) элемента.  
  
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
 Измерения, которого [тип](../properties/type-element-dimension-assl.md) задан равным *учетные записи*, могут иметь атрибут, определяющий тип учетной записи, например доходы или расходы и так далее, представленный членами в измерении. Затем используется тип учетной записи [мер](../objects/measure-element-assl.md) элементов, которого [AggregationFunction](../properties/aggregatefunction-element-assl.md) задан равным *ByAccount*, для определения статистической функции для использования при в статистической обработке элементов этого измерения. Элемент `Accounts` хранит коллекцию элементов `Account`, которые представляют типы счетов и статистическую функцию, предназначенную для использования с каждым типом счета.  
  
 Тип учетной записи, которые должны быть перечислены, если Агрегатная функция отличается от используемого по умолчанию [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] для каждого типа счета.  
  
 Набор допустимых типов счетов фиксирован.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AccountCollection>.  
  
## <a name="see-also"></a>См. также  
 [Элемент AccountType &#40;ASSL&#41;](../properties/accounttype-element-assl.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  