---
title: "Элемент ConnectionStringSecurity (ASSL) | Документы Microsoft"
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
apiname: ConnectionStringSecurity Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ConnectionStringSecurity
helpviewer_keywords: ConnectionStringSecurity element
ms.assetid: f25c4448-bb0d-4945-bc84-9c015eefa0eb
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d001daaacb06528c0baadde69e452fc917ce819b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="connectionstringsecurity-element-assl"></a>Элемент ConnectionStringSecurity (ASSL)
  Указывает, исключается ли пароль пользователя из строки подключения для источника данных в целях безопасности.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataSource>  
   ...  
   <ConnectionStringSecurity>...</ConnectionStringSecurity>  
   ...  
</DataSource>  
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
|Родительский элемент|[Источник данных](../../../analysis-services/scripting/objects/datasource-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*PasswordRemoved*|Из строки подключения удален пароль.|  
|*Без изменений*|Строка подключения не изменялась.|  
  
 Перечисление, соответствующее разрешенным значениям для **ConnectionStringSecurity** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ConnectionStringSecurity>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
