---
title: Элемент Password (ASSL) | Документы Microsoft
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
- Password Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Password element
ms.assetid: ee756b01-fb08-4a9a-8c2a-7c04af0f8658
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e702e7307e11c506652e91ca4cdc8f02ca06318d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087447"
---
# <a name="password-element-assl"></a>Элемент Password (ASSL)
  Содержит пароль учетной записи пользователя для [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ImpersonationInfo  
   ...  
  <Password>...</Password>  
   ...  
</ImpersonationInfo>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение `Password` элемент, а также значение [учетной записи](account-element-impersonationinfo-assl.md) элемент, используется для олицетворения, если значение [ImpersonationMode](impersonationmode-element-assl.md) элемента для любого элемента, производного от `ImpersonationInfo` тип данных имеет значение *ImpersonateAccount*.  
  
 Пустое значение для элемента `Password` могут предоставлять только члены роли администратора сервера для экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Элемент DataSourceImpersonationInfo &#40;ASSL&#41;](impersonationinfo-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  