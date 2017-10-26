---
title: "Выполнить метод (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Execute Method
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- EXECUTE
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.execute
- urn:schemas-microsoft-com:xml-analysis#Execute
helpviewer_keywords:
- Execute method
ms.assetid: 0fff5221-7164-4bbc-ab58-49cf04c52664
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 22bf60ae16e6b4e5f30bf694505e77857b6c0600
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="xml-elements---methods---execute"></a>Элементы XML - методы — выполнение
  Отправляет XML для аналитики (XMLA) команды для экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Сюда входят запросы, связанные с передачей данных, например извлечение или обновление данных на сервере.  
  
 **Пространство имен** urn:schemas-microsoft-com:xml-analysis  
  
 **Действие SOAP** "urn:schemas-microsoft-com:xml-analysis:Execute"  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Execute>  
   <Command>...</Command>  
   <Properties>...</Properties>  
   <Parameters>...</Parameters>  
</Execute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который появляется только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|None|  
|Дочерние элементы|[Команда](../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md), [параметры](../../analysis-services/xmla/xml-elements-properties/parameters-element-xmla.md), [свойства](../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 **Execute** метод выполняет команды XMLA, предоставленные в **команда** элемент и возвращает результат с помощью XML для Аналитики [строк](../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md) типа данных (для табличных результатов Задает) или XML для Аналитики [MDDataSet](../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) тип данных (для многомерных результирующих наборов.)  
  
## <a name="example"></a>Пример  
 Следующий образец кода демонстрирует вызов метода **Execute** , содержащего многомерное выражение (MDX) в инструкции SELECT.  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Statement>  
         SELECT [Measures].MEMBERS ON COLUMNS FROM [Adventure Works]  
      </Statement>  
   </Command>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Multidimensional</Format>  
         <AxisFormat>ClusterFormat</AxisFormat>  
      </PropertyList>  
   </Properties>  
</Execute>  
```  
  
## <a name="see-also"></a>См. также:  
 [Типы данных XML &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Обнаружение метод &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)   
 [Методы &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [XML-элементы &#40; XML для Аналитики &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Службы Analysis Services наборы строк схемы](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  

