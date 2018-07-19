---
title: Элемент Password (ASSL) | Документация Майкрософт
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: cc5464e4530e00a0d12807cb0cef2c2e1aa22afa
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050672"
---
# <a name="password-element-assl"></a>Элемент Password (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит пароль учетной записи пользователя для [ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md) элемент.  
  
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
|Родительский элемент|[ImpersonationInfo](../../../analysis-services/scripting/data-type/impersonationinfo-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение **пароль** элемент, а также значение [учетной записи](../../../analysis-services/scripting/properties/account-element-impersonationinfo-assl.md) элемент, используется для олицетворения, если значение [ImpersonationMode](../../../analysis-services/scripting/properties/impersonationmode-element-assl.md) -элемент для любой элемент производным от **ImpersonationInfo** установлен тип данных *ImpersonateAccount*.  
  
 Только члены роли администратора сервера для [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра можно указать пустое значение для **пароль** элемент  
  
## <a name="see-also"></a>См. также  
 [Элемент DataSourceImpersonationInfo &#40;ASSL&#41;](../../../analysis-services/scripting/properties/datasourceimpersonationinfo-element-assl.md)   
 [Свойства &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
