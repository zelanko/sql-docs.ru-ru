---
title: Целевой элемент (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Target Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.target
- http://schemas.microsoft.com/analysisservices/2003/engine#Target
- urn:schemas-microsoft-com:xml-analysis#Target
helpviewer_keywords:
- Target element
ms.assetid: 9a69a777-5f34-4e94-b470-6bab2a98df8b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97d198e823acb9bf3c8915e18cbf723032f81b58
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079794"
---
# <a name="target-element-xmla"></a>Элемент Target (XML для аналитики)
  Представляет целевой секции для слияния во время [MergePartitions](../xml-elements-commands/mergepartitions-element-xmla.md) команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MergePartitions>  
   <Target>  
      <DatabaseID>...</DatabaseID>  
      <CubeID>...</CubeID>  
      <MeasureGroupID>...</MeasureGroupID>  
      <PartitionID>...</PartitionID>  
   </Target>  
</MergePartitions>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-N: обязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[MergePartitions](../xml-elements-commands/mergepartitions-element-xmla.md)|  
|Дочерние элементы|[CubeID](id-element-xmla.md), [DatabaseID](databaseid-element-xmla.md), [MeasureGroupID](measuregroupid-element-xmla.md), [PartitionID](partitionid-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 `Target` Элемент – ссылка объекта в одну секцию, в которой содержимое исходных секций, определяемое [источников](sources-element-xmla.md) родителя `MergePartitions` элемент, объединяемые.  
  
## <a name="example"></a>Пример  
 В следующем примере все четыре секции группы мер Internet Sales объединяются в целевую секцию `Internet_Sales_2004`. В этом примере используется куб [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] из образца базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
```  
<MergePartitions xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
     <Source>  
        <DatabaseID>database</DatabaseID>  
        <CubeID>Adventure Works DW</CubeID>  
        <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
        <PartitionID>Internet_Sales_2001</PartitionID>  
     </Source>  
     <Source>  
      <DatabaseID>database</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2002</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>database</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2003</PartitionID>  
    </Source>  
  </Sources>  
  <Target>    <DatabaseID>database</DatabaseID>    <CubeID>Adventure Works DW</CubeID>    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>    <PartitionID>Internet_Sales_2004</PartitionID>  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a>См. также  
 [Элемент Source &#40;XML для Аналитики&#41;](source-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
