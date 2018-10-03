---
title: Элемент aliases (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Aliases Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Aliases
helpviewer_keywords:
- Aliases element
ms.assetid: 9de9e683-d30d-4d61-b32d-c5a946825742
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4783d4d24c383864efb212f512e24ceeb8b842b2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049094"
---
# <a name="aliases-element-assl"></a>Элемент Aliases (ASSL)
  Содержит коллекцию элементов [псевдоним](../properties/alias-element-assl.md) элементы, связанные с [учетной записи](../objects/account-element-assl.md) элемент  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Account>  
      ...  
   <Aliases>  
      <Alias>...</Alias>  
      </Aliases>  
      ...  
</Account>  
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
|Родительские элементы|[Учетная запись](../objects/account-element-assl.md)|  
|Дочерние элементы|[Псевдоним](../properties/alias-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `Aliases` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>См. также  
 [Учетные записи элемент &#40;ASSL&#41;](accounts-element-assl.md)   
 [Элемент Database описания &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
