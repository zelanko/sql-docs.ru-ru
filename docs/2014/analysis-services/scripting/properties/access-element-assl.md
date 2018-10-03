---
title: Доступ к элементу (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Access Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Access
helpviewer_keywords:
- Access element
ms.assetid: 6ad99010-fac5-48e9-a099-ecbca380e127
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 60fbf476e1d884cce28dd674ab16d3bda001a3a0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051844"
---
# <a name="access-element-assl"></a>Элемент Access (ASSL)
  Указывает уровень доступа для [CellPermission](../objects/cellpermission-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CellPermission>  
   ...  
   <Access>...</Access>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CellPermission](../objects/cellpermission-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Данный элемент может принимать значение одной из строк, перечисленных в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Чтение*|Допускается доступ только для чтения.|  
|*Производное чтение*|Допускается доступ на производное чтение.|  
|*ReadWrite*|Допускается доступ для чтения и записи.|  
  
 Перечисление, соответствующее допустимым значениям элемента `Access` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.CellPermissionAccess>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Role &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
