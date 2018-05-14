---
title: Элемент Property (CSDLBI) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 48262a12e13f548e96e765b785b85f556419ff24
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="property-element-csdlbi"></a>Элемент Property (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Элемент Property в CSDLBI — сложный тип, предоставляющий дополнения к элементу языка CSDL Property для моделей данных бизнес-аналитики.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент CSDLBI Property.  
  
|Название|Обязателен|Описание|  
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
 **Табличные**  
  
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
 **Многомерные**  
  
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
  
  
