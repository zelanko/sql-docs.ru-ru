---
title: Элемент ObjectDefinition (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ObjectDefinition Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#ObjectDefinition
- http://schemas.microsoft.com/analysisservices/2003/engine#ObjectDefinition
- microsoft.xml.analysis.objectdefinition
helpviewer_keywords:
- ObjectDefinition element
ms.assetid: 1911868c-a018-4308-8cf9-972a57f610a1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bc2b42ca96ef57bc46e5c04a5bc1f7528493aa83
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48214144"
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ALTER](../xml-elements-commands/alter-element-xmla.md), [Создание](../xml-elements-commands/create-element-xmla.md)|  
|Дочерние элементы|Обязательные элементы ASSL. Один или несколько элементов ASSL, используемых для определения объектов служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Дополнительные сведения о ASSL см. в разделе [свойства &#40;XMLA&#41;](xml-elements-properties.md).|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
 В следующем примере в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] создается пустая база данных с именем `Test Database`.  
  
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
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
