---
title: Элемент ImpersonationMode (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 786bc8e9ededa556d6d66d75e8e2cc52315cc62a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="impersonationmode-element-assl"></a>Элемент ImpersonationMode (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит значение, указывающее метод олицетворения для элементов, которые являются производными от [ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md) тип данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ImpersonationInfo>  
   ...  
   <ImpersonationMode>...</ImpersonationMode>  
  
</ImpersonationInfo>...  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Default*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Default*|В родительском объекте используется метод олицетворения, наиболее подходящий для контекста, в котором применяется олицетворение.|  
|*ImpersonateAccount*|В родительском объекте используются учетные данные учетной записи пользователя, которая указана в родительском элементе.|  
|*ImpersonateAnonymous*|В родительском объекте используются учетные данные анонимного пользователя.|  
|*ImpersonateCurrentUser*|В родительском объекте используются учетные данные текущего пользователя.|  
|*ImpersonateServiceAccount*|В родительском объекте используются учетные данные учетной записи службы, которая связана с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
 Перечисление, соответствующее разрешенным значениям для **ImpersonationMode** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ImpersonationLevel>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
