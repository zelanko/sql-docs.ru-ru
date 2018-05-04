---
title: Тип данных RelationalDataSource (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- RelationalDataSource Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- RelationalDataSource
helpviewer_keywords:
- RelationalDataSource data type
ms.assetid: 2b99d7d0-731d-4506-8c37-678a5dc29c8a
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7aa8cb57e5ad49159708f34cc4b935c53a5c5f5e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="relationaldatasource-data-type-assl"></a>Тип данных RelationalDataSource (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет производный тип данных, представляющий элемент [DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md) , основанный на реляционном источнике данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<RelationalDataSource>  
   <!-- Child elements are only those inherited from DataSource -->  
</RelationalDataSource>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Источник данных](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|[Источник данных](../../../analysis-services/scripting/objects/datasource-element-assl.md) ([DataSources](../../../analysis-services/scripting/collections/datasources-element-assl.md) коллекцию [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.RelationalDataSource>.  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
