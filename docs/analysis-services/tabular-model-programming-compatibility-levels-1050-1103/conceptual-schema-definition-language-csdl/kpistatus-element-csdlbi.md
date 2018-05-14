---
title: Элемент KpiStatus (CSDLBI) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bd4766295a985948572ce17702a86d3e53adb747
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="kpistatus-element-csdlbi"></a>Элемент KpiStatus (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Элемент KpiStatus определяет ссылку на столбец, который содержит значение, используемое в качестве индикатора состояния в составе ключевого показателя эффективности (KPI).  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент KpiStatus.  
  
|Название|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|PropertyRef|Да|Ссылка на столбец, содержащий значение, которое используется в качестве индикатора состояния в ключевом показателе эффективности.<br /><br /> Этот элемент ДОЛЖЕН включать ровно одну ссылку на столбец в соответствии с типом TPropertyRefcomplex.|  
  
## <a name="example"></a>Пример  
 **Табличные**  
  
 В следующем примере для CSDLBI версии 1.1 представлен ключевой показатель эффективности из примера табличной модели AdventureWorks. Элемент KpiStatus ссылается на столбец (представленный как PropertyRef), содержащий значение.  
  
```  
  
<Property Name="InternetCurrSalesPerf" Type="Double">  
   <bi:Measure>  
     <bi:Kpi StatusGraphic="Three Stars Colored">  
       <bi:KpiGoal>  
         <bi:PropertyRef Name="v_InternetCurrSalesPerf_Goal" />  
       </bi:KpiGoal>  
       <bi:KpiStatus>  
         <bi:PropertyRef Name="v_InternetCurrSalesPerf_Status" />  
       </bi:KpiStatus>  
     </bi:Kpi>  
   </bi:Measure>  
</Property>  
  
```  
  
## <a name="example"></a>Пример  
 **Многомерные**  
  
 В следующем примере для CSDLBI версии 1.1 показан ключевой показатель эффективности из куба операций Contoso. Элемент KpiStatus ссылается на меру, которая вычисляет значение для состояния ключевого показателя эффективности.  
  
```  
<bi:Measure   
       Caption="Sum of SalesAmount"   
       ReferenceName="Sum of SalesAmount"   
       FormatString="\$#,0.00;(\$#,0.00);\$#,0.00">  
  
    <bi:Kpi   
       StatusGraphic="Three Circles Colored">  
  
      <bi:KpiGoal>  
         <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Goal" />  
       </bi:KpiGoal>  
  
       <bi:KpiStatus>  
          <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Status" />  
        </bi:KpiStatus>  
  
       </bi:Kpi>  
</bi:Measure>  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Элемент KPI & #40; CSDLBI & #41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/kpi-element-csdlbi.md)  
  
  
