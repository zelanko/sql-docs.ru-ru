---
title: "Элемент ManagedProvider (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ManagedProvider Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: ManagedProvider element
ms.assetid: ed5a1077-20a4-40b9-b62d-0db0d53b9624
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b69ad147dd838a0811f29f3d1a42b88c0b17685f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="managedprovider-element-assl"></a>Элемент ManagedProvider (ASSL)
  Содержит имя управляемого поставщика, используемого элементом, производным от [DataSource](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md) тип данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataSource>  
   ...  
   <ManagedProvider>...</ManagedProvider>  
   ...  
</DataSource>  
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
|Родительский элемент|[Источник данных](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Если источник данных использует управляемый поставщик, элемент **ManagedProvider** содержит имя этого управляемого поставщика.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Name &#40; ASSL &#41;](../../../analysis-services/scripting/properties/name-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
