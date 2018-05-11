---
title: Элемент Schema (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9822bbf6112673c5e03c382063af2ed017b8d5ca
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
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
  
## <a name="remarks"></a>Примечания  
 **Схемы** представляется в формате языка определения схемы XML (XSD) наборов данных в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework, с некоторыми расширениями для наборов данных и других в рамках определения данных Language (DDL). Наборы данных определяют гибкое сопоставление между определением XSD и реляционной схемой, а затем возвращают определение XSD в более канонической форме. Только эта каноническая форма является допустимой для использования в источниках данных.  
  
 Элемент, соответствующий родителю параметра **схемы** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.DataSourceView>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
