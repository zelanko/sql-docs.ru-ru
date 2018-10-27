---
title: Слияние секций (XMLA) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 419ebd0d67b65213fde7393430aedec14249b2ae
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50147909"
---
# <a name="merging-partitions-xmla"></a>Слияние секций (XMLA)
  Если секции имеют одинаковые статистические схемы и структуры, можно объединить секции с помощью [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) в XML для аналитики (XMLA) команду. При управлении секциями их слияние является важным действием, особенно для тех секций, в которых содержатся исторические данные, секционированные по дате.  
  
 Например, в финансовом кубе может быть две секции.  
  
-   Одна секция представляет финансовые данные по текущему году, используя для обеспечения высокой производительности параметры хранения реляционной OLAP (ROLAP) в реальном времени.  
  
-   Другая секция содержит финансовые данные по предыдущим годам, используя параметры хранения многомерной OLAP (MOLAP) для обеспечения хранения.  
  
 В двух секциях установлены разные параметры хранения, но одинаковые статистические схемы. Вместо обрабатывать куб по годам исторических данных в конце года, вы можете использовать **MergePartitions** команду, чтобы слияние секции за текущий год в секцию за предыдущие годы. В этом случае будут сохранены данные статистических вычислений; при этом не требуется полной обработки куба, на что может уйти много времени.  
  
## <a name="specifying-partitions-to-merge"></a>Указание секций для слияния  
 При **MergePartitions** команда выполнена, статистической обработки данных, хранящихся в исходных секций, указанных в [источника](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) свойство добавляется в целевую секцию, указанную в [целевой объект ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) свойство.  
  
> [!NOTE]  
>  **Источника** свойство может содержать несколько ссылок объектов на секции. Тем не менее **целевой** свойства невозможно.  
  
 Для успешного слияния, секции, указываемые в обоих **источника** и **целевой** должен находиться в одной группе мер и использовать одинаковые статистические схемы. В противном случае возникает ошибка.  
  
 Секции, указываемые в **источника** удаляются после выполнения **MergePartitions** успешного выполнения команды.  
  
## <a name="examples"></a>Примеры  
  
### <a name="description"></a>Описание  
 В следующем примере объединяются все секции в **Customer Counts** группе мер **Adventure Works** кубе **Adventure Works DW** пример [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных в **Customers_2004** секции.  
  
### <a name="code"></a>Код  
  
```  
<MergePartitions xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2001</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2002</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2003</PartitionID>  
    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a>См. также  
 [Разработка с использованием XMLA в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
