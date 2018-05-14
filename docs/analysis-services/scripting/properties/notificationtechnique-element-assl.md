---
title: Элемент NotificationTechnique (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 23b8d193c3039a9606c0d0a0912829534e9673a3
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="notificationtechnique-element-assl"></a>Элемент NotificationTechnique (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Указывает, является ли [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или внешним клиентским приложением обрабатывает уведомления.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ProactiveCachingBinding>  
   <NotificationTechnique>...</NotificationTechnique>  
</ProactiveCachingBinding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Клиент*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ProactiveCachingBinding](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Клиент*|Внешнее клиентское приложение обрабатывает уведомление.|  
|*Server*|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] обрабатывает уведомление.|  
  
 Элемент, соответствующий родителю параметра **NotificationTechnique** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ProactiveCachingBinding>.  
  
 Перечисление, соответствующее разрешенным значениям для **NotificationTechnique** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.NotificationTechnique>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных ProactiveCachingBinding & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)  
  
  
