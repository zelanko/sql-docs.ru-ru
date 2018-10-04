---
title: Элемент invocation (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Invocation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Invocation
helpviewer_keywords:
- Invocation element
ms.assetid: f6bf64ad-ae57-4d46-bf92-1d07a65378bb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a67774a17518e44fa78c0caf639103bfb19de5e1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48108954"
---
# <a name="invocation-element-assl"></a>Элемент Invocation (ASSL)
  Указывает, каким образом [действие](../objects/action-element-assl.md) должны вызываться.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Action>  
   ...  
   <Invocation>...</Invocation>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Интерактивный*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Действие](../objects/action-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Вызов действия зависит от клиентского приложения. `Invocation` Предлагает клиентскому приложению способ обработки действия и не указывает на экземпляр [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] как для вызова действия.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Интерактивный*|Вызывается интерактивно пользователем.|  
|*OnOpen*|Вызывается при открытии объекта клиентским приложением.|  
|*Пакетной службы*|Вызывается командой пакетной обработки.|  
  
 Перечисление, соответствующее допустимым значениям элемента `Invocation` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
