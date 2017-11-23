---
title: "Элемент ObjectDefinition (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ObjectDefinition Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#ObjectDefinition
- http://schemas.microsoft.com/analysisservices/2003/engine#ObjectDefinition
- microsoft.xml.analysis.objectdefinition
helpviewer_keywords: ObjectDefinition element
ms.assetid: 1911868c-a018-4308-8cf9-972a57f610a1
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9dfdfbf039d9c6f4dde19f89c7cb1d5326339491
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="objectdefinition-element-xmla"></a>Элемент ObjectDefinition (XML для аналитики)
  Содержит один или несколько элементов языка сценариев служб Analysis Services (ASSL), используемых для создания или изменения объектов в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Create> <!-- or Alter -->  
   ...  
   <ObjectDefinition>  
      <!-- One or more ASSL elements -->  
   </ObjectDefinition>  
   ...  
</Create>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ALTER](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md), [создания](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)|  
|Дочерние элементы|Обязательные элементы ASSL. Один или несколько элементов ASSL, используемых для определения объектов служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Дополнительные сведения о ASSL см. в разделе [свойства &#40; XML для Аналитики &#41; ](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md).|  
  
## <a name="remarks"></a>Замечания  
  
## <a name="example"></a>Пример  
 В следующем примере создается пустая база данных с именем **тестовую базу данных** на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.  
  
```  
  
      <Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
   <ObjectDefinition>  
      <Database xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
         <Name>Test Database</Name>  
         <Description>A test database.</Description>  
      </Database>  
   </ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
