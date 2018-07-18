---
title: Метод (XMLA) Discover | Документация Майкрософт
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 921afc6d17a0eddcba48e5a6a6064810a3b3b6ef
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979109"
---
# <a name="xml-elements---methods---discover"></a>XML-элементы — методы — обнаружение
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Извлекает сведения, такие как список доступных баз данных или сведения о конкретном объекте от экземпляра служб Analysis Services. Данные, полученные с помощью метода **Discover** , зависят от значений параметров, переданных этому методу.  
  
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
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|None|  
|Дочерние элементы|[Свойства](../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md), [RequestType](../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md), [ограничения](../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 **Discover** метод запрашивает метаданные об экземплярах и объектах. Метаданные возвращаются с помощью XML для Аналитики [набора строк](../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md) тип данных.  
 
> [!TIP] 
> Если вы не знакомы с XML-команды, щелкните шаблон запроса XML для Аналитики **запроса** панели инструментов в среде Management Studio для построения запроса и добавить параметры. Дополнительные сведения см. в статье [Use Analysis Services Templates in SQL Server Management Studio](../../analysis-services/instances/use-analysis-services-templates-in-sql-server-management-studio.md). 
  
## <a name="example"></a>Пример  
 В следующем образце кода, клиент отправляет **Discover** вызов для получения списка кубов [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] образца базы данных служб Analysis Services:  
  
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
 [Типы данных XML &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Метод Execute &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)   
 [Методы &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [XML-элементов &#40;XML для Аналитики&#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Наборы строк схемы служб Analysis Services](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
