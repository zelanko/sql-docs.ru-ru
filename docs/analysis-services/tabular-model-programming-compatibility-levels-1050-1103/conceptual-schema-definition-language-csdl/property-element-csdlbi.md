---
title: "Элемент Property (CSDLBI) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: f0770c5e-6420-4d0c-a5bf-b94eaf6877ca
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d61770b935ad397d5d0db48a3651f143ebef5522
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="property-element-csdlbi"></a>Элемент Property (CSDLBI)
  Элемент Property в CSDLBI — сложный тип, предоставляющий дополнения к элементу языка CSDL Property для моделей данных бизнес-аналитики.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент CSDLBI Property.  
  
|Имя|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Содержание|Нет|Строка, которая содержит код языка запроса.|  
|DefaultAggregationFunction|Да|Строка, указывающая агрегатную функцию, которая должна использоваться при вычислениях с атрибутом, если никакой другой функции не задано.<br /><br /> Если этот параметр не указан, используется статистическое вычисление по умолчанию для модели — обычно SUM.|  
|GroupingBehavior|Нет|Значение, указывающее, как группируются результаты запроса. Содержимое атрибута определено простым типом TGroupingBehavior (см. таблицу ниже).|  
|OrderBy|Нет|Ссылка на другое свойство в модели, определяющее порядок сортировки для значений этого свойства.<br /><br /> Значения для двух свойств ДОЛЖНЫ иметь сопоставление «один к одному». В противном случае поведение сортировки будет неопределенным.<br /><br /> Если этот элемент не указан, свойства сортируются по их значениям.|  
|Стабильность|Нет|Атрибут, указывающий стабильность значений свойства между операциями обновления.<br /><br /> Этот атрибут не устанавливается пользователями, а формируется средой разработки только для неустойчивых значений. Всегда применяется к столбцам, которые содержат номер строки, и столбцам, которые содержат формулы, создающие неопределенные результаты, например NOW() или RAND().<br /><br /> Значения для этого атрибута перечислены в следующей таблице, описывающей тип Stabilitysimple.|  
  
## <a name="groupingbehavior"></a>GroupingBehavior  
 В следующей таблице перечислены значения простого типа GroupingBehavior.  
  
|Значение|Description|  
|-----------|-----------------|  
|GroupOnValue|Группирование по значению атрибута xthe.|  
|GroupOnEntityKey|Группирование по ключу сущности.|  
  
 В следующем примере показано использование этих двух значений. Предположим, запрос был разработан для определения заработной платы конкретного пользователя, указанного по имени. Если база данных содержит двух пользователей с одинаковым именем, но разными идентификаторами базы данных, результаты запроса будут отличаться в зависимости от значения атрибута, которое применяется к столбцу.  
  
-   **GroupOnValue**: запрос, результаты содержат определения зарплаты обоих пользователей, подытоженные вместе.  
  
-   **GroupOnEntityKey**: запрос, результаты содержат определения зарплаты для каждого пользователя, но перечисленные по отдельности.  
  
## <a name="stability"></a>Стабильность  
 В следующей таблице перечислены значения **стабильности** простого типа.  
  
|Значение|Description|  
|-----------|-----------------|  
|Stable|Свойство не меняется между операциями обновления.|  
|RowNumber|Свойство содержит номер строки.|  
|Временный|Свойство не может оставаться константным между операциями обновления.|  
  
## <a name="example"></a>Пример  
 **Табличный**  
  
 В следующем коде XML показано представление для CSDLBI версии 1.1 некоторых свойств в примере табличной модели AdventureWorks.  
  
```  
  
<EntityType   
   Name="DimEmployee">  
   <Key>  
      <PropertyRef   
      Name="RowNumber" />  
   </Key>  
  
   <Property   
      Name="RowNumber"   
      Type="Int64"   
      Nullable="false">  
   <bi:Property   
      Hidden="true"   
      Contents="RowNumber"   
      Stability="RowNumber" />  
   </Property>  
  
   <Property   
      Name="EmployeeKey"   
      Type="Int64">  
   <bi:Property />  
   </Property>  
….  
</bi:EntityType>  
</EntityType>  
  
```  
  
## <a name="example"></a>Пример  
 **Multidimensional**  
  
 В следующем примере для CSDLBI версии 1.1 показаны некоторые свойства столбцов в модели данных, представляющей куб операций Contoso. Обратите внимание, что заметки бизнес-аналитики не являются необходимыми и применяются не к большинству столбцов, а только к требующим специальной обработки на уровне представления данных.  
  
```  
  
<EntityType   
   Name="Bike">  
  
   <Key>  
      <PropertyRef Name="RowNumber" />  
   </Key>  
  
   <Property   
      Name="RowNumber"   
      Type="Int64"   
      Nullable="false">  
   <bi:Property   
      Hidden="true"   
      Contents="RowNumber"   
      Stability="RowNumber"   
   />  
   </Property>  
  
   <Property   
      Name="ProductAlternateKey"   
      Type="String"   
      MaxLength="Max"   
      Unicode="true"   
      FixedLength="false">  
   <bi:Property />  
   </Property>  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Технический справочник по заметки бизнес-Аналитики для языка CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  

