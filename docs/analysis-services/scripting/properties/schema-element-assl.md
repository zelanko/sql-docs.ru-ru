---
title: Элемент Schema (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
manager: kfile
ms.openlocfilehash: 398663809007eb7fdd51e12f2c653345b898b2b4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="schema-element-assl"></a>Элемент Schema (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Тип данных и длина|Схема|  
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
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
