---
title: Элемент KPI (CSDLBI) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bc368aed1186c20e76ce643a33673030713547ba
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="kpi-element-csdlbi"></a>Элемент KPI (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  В элементе Kpi определяется вычисление, которое может быть использовано в качестве ключевого показателя эффективности (KPI). В модели данных бизнес-аналитики ключевые показатели эффективности (KPI) основаны на мерах, поэтому определение KPI содержит все метаданные, связанные с мерами, а также сведения, необходимые для представления значений KPI, в том числе рисунок по умолчанию.  
  
 В элементе Kpi не указывается формула, содержащаяся в определении меры, однако указаны дополнительные метаданные, связанные с мерами, используемыми в качестве ключевых показателей эффективности. Обозначив меру в качестве ключевого показателя эффективности, уже нельзя использовать ее в других контекстах.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент ключевого показателя эффективности.  
  
|Название|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Документация|Нет|Описание ключевого показателя эффективности.|  
|KpiGoal|Да|Ссылка на столбец, содержащий значения, которые могут быть использованы в качестве цели.<br /><br /> См. раздел [Элемент PropertyRef (CSDLBI)](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/propertyref-element-csdlbi.md).|  
|KpiStatus|Да|Ссылка на столбец, содержащий значения, которые представляют текущее состояние ключевого показателя эффективности.|  
|StatusGraphic|Да|Ссылка на изображение, которое указывает на отрицательный, нейтральный или положительный результат выполнения с учетом целей, определенных в качестве ключевого показателя эффективности.|  
  
## <a name="remarks"></a>Замечания  
 При разработке модели можно создать ключевой показатель эффективности,, создав меру и назначив ее в качестве ключевого показателя эффективности. Затем добавляются сведения, относящиеся к ключевым показателям эффективности, например рисунок, который используется при отображении трендов.  
  
## <a name="example"></a>Пример  
 **Табличные**  
  
 В следующем примере CSDLBI версии1.0 представлен ключевой показатель эффективности, с помощью которого измеряются продажи. Пример взят из образца табличной модели AdventureWorks.  
  
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
  
 В следующем примере для CSDLBI версии 1.1 показан ключевой показатель эффективности из куба операций Contoso.  
  
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
 [Технический справочник по заметки бизнес-Аналитики для языка CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
