---
title: Выполнить метод (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 019ac154ef902009405f11bcc7023ea831d1f71b
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="xml-elements---methods---execute"></a>Элементы XML - методы — выполнение
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
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
|Родительский элемент|Нет|  
|Дочерние элементы|[Команда](../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md), [параметры](../../analysis-services/xmla/xml-elements-properties/parameters-element-xmla.md), [свойства](../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
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
  
## <a name="see-also"></a>См. также  
 [Типы данных XML & #40; XML для Аналитики & #41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Метод Discover &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)   
 [Методы &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [XML-элементы & #40; XML для Аналитики & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Службы Analysis Services наборы строк схемы](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
