---
title: "Элемент PropertyRef (CSDLBI) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 8299efb9-e224-4a82-bdfc-a74ec92f8711
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9df2f9bfd77a854c90f08ed8b4314bfa212bf469
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="propertyref-element-csdlbi"></a>Элемент PropertyRef (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Элемент PropertyRef — простой тип, предоставляющий ссылку на столбец, предоставляющий значение, необходимое другому свойству.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент PropertyRef.  
  
|Имя|Обязателен|Description|  
|----------|-----------------|-----------------|  
|Имя|Да|Строка, содержащая имя свойства, являющегося целью ссылки.|  
  
## <a name="propertyrefs-element"></a>Элемент PropertyRefs  
 PropertyRefs — сложный тип, который определяет коллекцию свойств, где каждое свойство содержится в элементе PropertyRef.  
  
 В следующей таблице перечислены элементы и атрибуты типа PropertyRefs.  
  
|Имя|Обязателен|Description|  
|----------|-----------------|-----------------|  
|PropertyRef|Да|Значение типа String, содержащее ссылку на свойство.|  
  
## <a name="example"></a>Пример  
 **Табличный**  
  
 В следующем примере для CSDLBI версии 1.1 элемент PropertyRef указывает источник формулы, используемой в мере, из примера табличной модели AdventureWorks.  
  
```  
<bi:Measure Caption="Total Current Quarter Margin Performance" ReferenceName="Total Current Quarter Margin Performance" Width="0" IsSimpleMeasure="false">  
  <bi:Kpi StatusGraphic="Three Symbols UnCircled Colored">  
    <bi:KpiGoal>  
      <bi:PropertyRef Name="Measures___Total_Current_Quarter_Margin_Performance_Goal_" />  
    </bi:KpiGoal>  
    <bi:KpiStatus>  
      <bi:PropertyRef Name="Measures___Total_Current_Quarter_Margin_Performance_Status_" />  
    </bi:KpiStatus>  
  </bi:Kpi>  
</bi:Measure>  
```  
  
## <a name="example"></a>Пример  
 **Multidimensional**  
  
 В следующем примере для CSDLBI версии 1.1 показан ключевой показатель эффективности из куба операций Contoso. Элементы PropertyRef указывают на столбцы, содержащие формулы или значения, используемые для определения цели ключевого показателя эффективности и состояния относительно этой цели.  
  
```  
<Property Name="Sum_of_SalesAmount" Type="Decimal" Precision="19" Scale="4">  
   <Documentation>  
     <Summary>KPI Description</Summary>  
   </Documentation>  
     <bi:Measure   
         Caption="Sum of SalesAmount"   
         ReferenceName="Sum of SalesAmount"   
         FormatString="\$#,0.00;(\$#,0.00);\$#,0.00">  
     <bi:Kpi   
           StatusGraphic="Three Circles Colored">  
         <bi:KpiGoal>  
            <bi:PropertyRef Name="v_Sum_of_SalesAmount_Goal" />  
          </bi:KpiGoal>  
          <bi:KpiStatus>  
              <bi:PropertyRef Name="v_Sum_of_SalesAmount_Status" />  
          </bi:KpiStatus>  
     </bi:Kpi>  
     </bi:Measure>  
</Property>  
```  
  
## <a name="see-also"></a>См. также:  
 [Технический справочник по аннотациям бизнес-аналитики для языка CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
