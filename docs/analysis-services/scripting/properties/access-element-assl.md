---
title: Доступ к элементу (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 00bcd1f7cb86e66f521c0dd95c265225f4cf1ef1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="access-element-assl"></a>Элемент Access (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Указывает уровень доступа для [CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md) элемента.  
  
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
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Данный элемент может принимать значение одной из строк, перечисленных в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Чтение*|Допускается доступ только для чтения.|  
|*Производное чтение*|Допускается доступ на производное чтение.|  
|*ReadWrite*|Допускается доступ для чтения и записи.|  
  
 Перечисление, соответствующее разрешенным значениям для **доступа** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CellPermissionAccess>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Role & #40; ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
