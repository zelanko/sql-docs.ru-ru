---
title: Выполнение метода (XML для Аналитики) | Документация Майкрософт
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
- Execute Method
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec3fa458148638af5431b4a519acf8556d29b122
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37235564"
---
# <a name="execute-method-xmla"></a>Метод Execute (XML для аналитики)
  Отправляет команды XML для аналитики (XMLA) для экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Сюда входят запросы, связанные с передачей данных, например извлечение или обновление данных на сервере.  
  
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
|Дочерние элементы|[Команда](xml-elements-properties/command-element-xmla.md), [параметры](xml-elements-properties/parameters-element-xmla.md), [свойства](xml-elements-properties/properties-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 `Execute` Метод выполняет команды XMLA, предоставленные в `Command` элемент и возвращает результат с помощью XML для Аналитики [набора строк](xml-data-types/rowset-data-type-xmla.md) тип данных (для табличных результирующих наборов) или XML для Аналитики [MDDataSet](xml-data-types/mddataset-data-type-xmla.md) тип данных (для многомерных результирующих наборов.)  
  
## <a name="example"></a>Пример  
 Следующий образец кода демонстрирует вызов метода `Execute`, содержащего многомерное выражение (MDX) в инструкции SELECT.  
  
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
  
## <a name="see-also"></a>См. также  
 [Типы данных XML &#40;XML для Аналитики&#41;](xml-data-types/xml-data-types-xmla.md)   
 [Метод Discover &#40;XML для Аналитики&#41;](xml-elements-methods-discover.md)   
 [Методы &#40;XML для Аналитики&#41;](xml-elements-methods.md)   
 [XML-элементов &#40;XML для Аналитики&#41;](../dev-guide/xml-elements-xmla.md)   
 [Наборы строк схемы служб Analysis Services](../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
