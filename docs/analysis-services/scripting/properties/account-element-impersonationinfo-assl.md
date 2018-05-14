---
title: Учетная запись элемент (ImpersonationInfo) (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ce73dcfc07da406c01f1df0edce01da360ecd49a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="account-element-impersonationinfo-assl"></a>Элемент Account (ImpersonationInfo) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит имя учетной записи пользователя для [ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md) тип данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ImpersonationInfo  
   ...  
  <Account>...</Account>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение **учетной записи** элемент, а также значение [пароль](../../../analysis-services/scripting/properties/password-element-assl.md) элемент, используется для олицетворения, если значение [ImpersonationMode](../../../analysis-services/scripting/properties/impersonationmode-element-assl.md) элемент для любой элемент, производный от **ImpersonationInfo** тип данных имеет значение *ImpersonateAccount*.  
  
## <a name="see-also"></a>См. также  
 [Элемент DataSourceImpersonationInfo &#40;ASSL&#41;](../../../analysis-services/scripting/properties/datasourceimpersonationinfo-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
