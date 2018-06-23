---
title: Discover, метод (XMLA) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Discover Method
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.discover
- urn:schemas-microsoft-com:xml-analysis#Discover
- Discover
helpviewer_keywords:
- Discover method
ms.assetid: 0eb52d88-c081-416e-a229-610e4373b0b3
caps.latest.revision: 36
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: ead875bbe88ea71c8741450f8a3127efcf4b313d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188095"
---
# <a name="discover-method-xmla"></a>Метод Discover (XML для аналитики)
  Получает сведения, такие как список доступных баз данных или сведений о конкретном объекте от экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Данные, полученные с помощью метода `Discover`, зависят от значений параметров, переданных этому методу.  
  
 **Пространство имен** urn:schemas-microsoft-com:xml-analysis  
  
 **Действие SOAP** "urn:schemas-microsoft-com:xml-analysis:Discover"  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Discover>  
   <RequestType>...</RequestType>  
   <Restrictions>...</Restrictions>  
   <Properties>...</Properties>  
</Discover>  
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
|Родительский элемент|None|  
|Дочерние элементы|[Свойства](xml-elements-properties/properties-element-xmla.md), [RequestType](xml-elements-properties/type-element-xmla.md), [ограничения](xml-elements-properties/restrictions-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Метод `Discover` запрашивает метаданные об экземплярах и объектах служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Метаданные возвращаются с помощью XML для Аналитики [строк](xml-data-types/rowset-data-type-xmla.md) тип данных.  
  
## <a name="example"></a>Пример  
 Следующий образец кода демонстрирует вызов клиентом метода `Discover` для получения списка кубов в образце базы данных [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]:  
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <RequestType>MDSCHEMA_CUBES</RequestType>  
   <Restrictions>  
      <RestrictionList>  
         <CATALOG_NAME>Adventure Works DW Multidimensional 2012</CATALOG_NAME>  
      </RestrictionList>  
   </Restrictions>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Tabular</Format>  
      </PropertyList>  
   </Properties>  
</Discover>  
```  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML &#40;XML для Аналитики&#41;](xml-data-types/xml-data-types-xmla.md)   
 [Метод Execute &#40;XML для Аналитики&#41;](xml-elements-methods-execute.md)   
 [Методы &#40;XML для Аналитики&#41;](xml-elements-methods.md)   
 [XML-элементы &#40;XML для Аналитики&#41;](../dev-guide/xml-elements-xmla.md)   
 [Наборы строк схемы служб Analysis Services](../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  