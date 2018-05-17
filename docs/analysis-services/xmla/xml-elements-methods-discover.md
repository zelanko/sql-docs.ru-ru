---
title: Discover, метод (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 661d3bc1307c9a61e75c313347b1530031eb89f1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="xml-elements---methods---discover"></a>Элементы XML - методы — обнаружения
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
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
|Родительский элемент|Нет|  
|Дочерние элементы|[Свойства](../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md), [RequestType](../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md), [ограничения](../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
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
  
## <a name="see-also"></a>См. также  
 [Типы данных XML & #40; XML для Аналитики & #41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Метод Execute &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)   
 [Методы &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [XML-элементы & #40; XML для Аналитики & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Службы Analysis Services наборы строк схемы](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
