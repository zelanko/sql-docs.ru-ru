---
title: Элемент KPI (CSDLBI) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 203ee6e8-eef2-4476-b09f-bd95e492ddaa
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 40da96c5fa483f8e502352f52c51c26cdb34e8ad
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
  
