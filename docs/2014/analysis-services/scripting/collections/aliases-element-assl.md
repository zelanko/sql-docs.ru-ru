---
title: Элемент aliases (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 60673c26bf4a430c842da0fb61c98de7242ccd1c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188110"
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
 Элемент, соответствующий родительский `Aliases` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>См. также  
 [Учетные записи элемента &#40;ASSL&#41;](accounts-element-assl.md)   
 [Элемент Database &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  