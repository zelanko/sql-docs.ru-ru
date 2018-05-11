---
title: Элемент DataSourceView (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cbfe569455a726760a3ba1c20aa299d4863cf612
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="datasourceview-element-xmla"></a>Элемент DataSourceView (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит представление источника данных вне строки, которые привязки для родительского [пакета](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) или [процесс](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Batch> <!-- or Process>  
...  
   <DataSourceView>  
      <DatabaseID>...</DatabaseID>  
      <DataSourceViewID>...</DataSourceViewID>  
   </DataSourceView>  
...  
</Batch>  
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
|Родительские элементы|[Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md), [Process](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|Дочерние элементы|[DatabaseID](../../../analysis-services/xmla/xml-elements-properties/databaseid-element-xmla.md), [DataSourceViewID](../../../analysis-services/scripting/properties/datasourceviewid-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 **DataSourceView** элемент представляет привязку вне строки в представлении источника данных, используемые **пакета** или **процесс** для временного переопределения источника данных Просмотр привязки для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] объектов, обрабатываемых командой.  
  
 Дополнительные сведения о ожидания привязок см. в разделе [& #40; источники данных и привязки Многомерные службы SSAS & #41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
