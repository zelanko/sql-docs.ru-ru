---
title: "Discover, метод (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 09/14/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Discover Method
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.discover
- urn:schemas-microsoft-com:xml-analysis#Discover
- Discover
helpviewer_keywords:
- Discover method
ms.assetid: 0eb52d88-c081-416e-a229-610e4373b0b3
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 60a101afa2953d62e2910b4523a0213e4e786490
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="xml-elements---methods---discover"></a>Элементы XML - методы — обнаружения
  Получает сведения, такие как список доступных баз данных или сведений о конкретном объекте от экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Данные, полученные с помощью метода **Discover** , зависят от значений параметров, переданных этому методу.  
  
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
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|None|  
|Дочерние элементы|[Свойства](../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md), [RequestType](../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md), [ограничения](../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 **Discover** метод запрашивает метаданные об [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляров и объектов. Метаданные возвращаются с помощью XML для Аналитики [строк](../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md) тип данных.  
 
> [!TIP] 
> Если вы не знакомы с команды XML, щелкните шаблон запроса XML для Аналитики **запроса** инструментов в среде Management Studio для построения запроса и добавьте параметры. Дополнительные сведения см. в статье [Use Analysis Services Templates in SQL Server Management Studio](../../analysis-services/instances/use-analysis-services-templates-in-sql-server-management-studio.md). 
  
## <a name="example"></a>Пример  
 В следующем образце кода, клиент отправляет **Discover** вызов для запроса получения списка кубов из [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] пример [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных:  
  
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
  
## <a name="see-also"></a>См. также:  
 [Типы данных XML &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Выполнение метода &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)   
 [Методы &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [XML-элементы &#40; XML для Аналитики &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Службы Analysis Services наборы строк схемы](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  

