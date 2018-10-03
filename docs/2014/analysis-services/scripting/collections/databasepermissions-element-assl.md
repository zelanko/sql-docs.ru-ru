---
title: Элемент DatabasePermissions (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DatabasePermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DatabasePermissions
helpviewer_keywords:
- DatabasePermissions element
ms.assetid: c4ce0da3-f7ba-4f11-8cd8-236c32992aaf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9d92f794ecf77eabf1faf555fecb35040993937f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48092174"
---
# <a name="databasepermissions-element-assl"></a>Элемент DatabasePermissions (ASSL)
  Содержит коллекцию элементов [DatabasePermission](../objects/databasepermission-element-assl.md) элементы, связанные с [базы данных](../objects/database-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Database>  
   ...  
   <DatabasePermissions>  
      <DatabasePermission>...</DatabasePermission>  
      </DatabasePermissions>  
      ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[База данных](../objects/database-element-assl.md)|  
|Дочерние элементы|[DatabasePermission](../objects/databasepermission-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.DatabasePermissionCollection>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных Permission &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
