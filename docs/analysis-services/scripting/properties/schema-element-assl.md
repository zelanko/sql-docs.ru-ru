---
title: "Элемент Schema (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
apiname: Schema Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Schema
helpviewer_keywords: Schema element
ms.assetid: 4b6375fb-7ad8-4d5f-88b1-abd3da2654db
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a39f50d6c91a8f4a321c62943e8894777c376faf
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
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
  
  
