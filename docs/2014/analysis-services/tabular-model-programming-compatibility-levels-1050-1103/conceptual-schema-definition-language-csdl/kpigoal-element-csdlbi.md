---
title: Элемент KpiGoal (CSDLBI) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: fd8afbe7-b57d-4b47-862d-eb7b2489c327
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ceee819fb887e2a45b3f366b261fba00df4776a6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191384"
---
# <a name="kpigoal-element-csdlbi"></a>Элемент KpiGoal (CSDLBI)
  Элемент KpiGoal предоставляет ссылку на столбец, используемый для определения цели ключевого показателя эффективности (KPI).  
  
 В CSDLBI ключевые показатели эффективности основаны на мерах, а элемент "Мера" может содержать формулу, при этом другие метаданные, связанные с ключевым показателем эффективности (KPI), определяются как часть [элемента KPI (CSDLBI)](kpi-element-csdlbi.md).  Элемент Kpigoal — это подтип элемента Kpi.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены атрибуты, определяющие элементы KpiGoal.  
  
|Имя|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|PropertyRef|Да|Ссылка на столбец, содержащий значение цели ключевого индикатора эффективности.<br /><br /> Элемент Kpigoal должен содержать ровно один элемент PropertyRef.<br /><br /> См. раздел [Элемент PropertyRef (CSDLBI)](propertyref-element-csdlbi.md).|  
  
## <a name="example"></a>Пример  
 **Табличный**  
  
 В следующем примере для CSDLBI версии 1.1 представлен ключевой показатель эффективности из образца модели AdventureWorks.  
  
```  
  
<Property Name="InternetCurrentSalesPerformance" Type="Double">  
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
 **Multidimensional**  
  
 В следующем примере для CSDLBI версии 1.1 показан ключевой показатель эффективности из куба операций Contoso.  
  
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
  
## <a name="see-also"></a>См. также  
 [Элемент KPI &#40;CSDLBI&#41;](kpi-element-csdlbi.md)  
  
  
