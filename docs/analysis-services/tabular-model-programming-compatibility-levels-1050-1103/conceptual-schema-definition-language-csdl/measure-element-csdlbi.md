---
title: Измерения элемента (CSDLBI) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 31bcb52bb9d1d0cf90b81ddc39ea838b00ece02f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34039208"
---
# <a name="measure-element-csdlbi"></a>Элемент Measure (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Элемент «Мера» — сложный тип, основанный на элементе языка CSDL «Свойство». Заметки CSDLBI добавляют атрибуты, обеспечивающие определение сложных формул для использования в модели данных бизнес-аналитики.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице представлены элементы и атрибуты, определяющие элемент «Мера», в дополнение ко всем атрибутам, применимым к элементу «Свойство».  
  
|Название|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Kpi|Нет|Обязательный элемент только для мер, которые используются в качестве ключевых показателей эффективности. Не все меры являются ключевыми показателями эффективности, но все ключевые показатели эффективности должны быть основаны на определении меры.<br /><br /> [Элемент KPI & #40; CSDLBI & #41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/kpi-element-csdlbi.md)|  
|IsSimpleMeasure|Нет|Значение TRUE или FALSE, которое указывает, является ли формула, используемая в мере, одним из простых агрегатов (SUM, COUNT, MIN, MAX, AVG, DistinctCount).<br /><br /> Значение по умолчанию — true.|  
  
## <a name="example"></a>Пример  
 **Табличные**  
  
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
  
## <a name="see-also"></a>См. также:  
 [Технический справочник по заметки бизнес-Аналитики для языка CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
