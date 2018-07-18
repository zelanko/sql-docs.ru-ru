---
title: Измерить элемент (CSDLBI) | Документация Майкрософт
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
ms.assetid: bfbc9274-053a-421a-bb81-2095bba710be
caps.latest.revision: 10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0c3a2f2ef1c1dcc80e0b8ac9cb68ce5d5694d104
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224026"
---
# <a name="measure-element-csdlbi"></a>Элемент Measure (CSDLBI)
  Элемент «Мера» — сложный тип, основанный на элементе языка CSDL «Свойство». Заметки CSDLBI добавляют атрибуты, обеспечивающие определение сложных формул для использования в модели данных бизнес-аналитики.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице представлены элементы и атрибуты, определяющие элемент «Мера», в дополнение ко всем атрибутам, применимым к элементу «Свойство».  
  
|Имя|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Kpi|Нет|Обязательный элемент только для мер, которые используются в качестве ключевых показателей эффективности. Не все меры являются ключевыми показателями эффективности, но все ключевые показатели эффективности должны быть основаны на определении меры.<br /><br /> [Элемент KPI &#40;CSDLBI&#41;](kpi-element-csdlbi.md)|  
|IsSimpleMeasure|Нет|Значение TRUE или FALSE, которое указывает, является ли формула, используемая в мере, одним из простых агрегатов (SUM, COUNT, MIN, MAX, AVG, DistinctCount).<br /><br /> Значение по умолчанию — true.|  
  
## <a name="example"></a>Пример  
 **Табличный**  
  
 В следующем примере для CSDLBI версии 1.1 представлены две меры из образца табличной модели AdventureWorks. Вторая мера преобразована в ключевой показатель эффективности (KPI) путем добавления элементов KPI.  
  
```  
  
<Property   
    Name="Order_Lines_Count"   
    Type="Int64">  
<bi:Measure   
    Caption="Order Lines Count"   
    ReferenceName="Order Lines Count"   
    Width="0"   
    IsSimpleMeasure="false" />  
</Property>  
  
<Property   
    Name="Total_Current_Quarter_Sales_Performance"   
    Type="Double">  
<bi:Measure   
    Caption="Total Current Quarter Sales Performance"   
    ReferenceName="Total Current Quarter Sales Performance"   
    Width="0"   
    IsSimpleMeasure="false">  
    <bi:Kpi   
    StatusGraphic="Three Signs Colored">  
      <bi:KpiGoal>  
        <bi:PropertyRef Name="Measures___Total_Current_Quarter_Sales_Performance_Goal_" />  
      </bi:KpiGoal>  
      <bi:KpiStatus>  
        <bi:PropertyRef Name="Measures___Total_Current_Quarter_Sales_Performance_Status_" />  
      </bi:KpiStatus>  
    </bi:Kpi>  
  </bi:Measure>  
</Property>  
```  
  
## <a name="example"></a>Пример  
 **Multidimensiona;**  
  
 В следующем примере для CSDLBI версии 1.1 представлена мера из куба операций Contoso, используемая в качестве ключевого показателя эффективности.  
  
```  
  
<Property   
    Name="Sum_of_SalesAmount"   
    Type="Decimal" Precision="19" Scale="4">  
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
  
## <a name="see-also"></a>См. также  
 [Технический справочник по аннотациям бизнес-аналитики для языка CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
