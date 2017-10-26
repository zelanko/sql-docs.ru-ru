---
title: "Элемент Schema (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Schema Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Schema
helpviewer_keywords:
- Schema element
ms.assetid: 4b6375fb-7ad8-4d5f-88b1-abd3da2654db
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 51fd142bad60a7c8e64d27952509dfa5b2b6c28f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="schema-element-assl"></a>Элемент Schema (ASSL)
  Содержит схему представления источников данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataSourceView>  
   ...  
   <Schema>...</Schema>  
   ...  
</DataSourceView>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|схема|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **Схемы** представляется в формате языка определения схемы XML (XSD) наборов данных в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework, с некоторыми расширениями для наборов данных и других в рамках определения данных Language (DDL). Наборы данных определяют гибкое сопоставление между определением XSD и реляционной схемой, а затем возвращают определение XSD в более канонической форме. Только эта каноническая форма является допустимой для использования в источниках данных.  
  
 Элемент, соответствующий родителю параметра **схемы** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.DataSourceView>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

