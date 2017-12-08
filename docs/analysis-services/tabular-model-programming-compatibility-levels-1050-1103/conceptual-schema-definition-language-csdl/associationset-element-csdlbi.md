---
title: "Элемент AssociationSet (CSDLBI) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
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
applies_to: SQL Server 2016 Preview
ms.assetid: 93e5ac4d-d7e8-490e-b775-28263a48cfcc
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ae30edd006aa425ddd4f574ceb67f0534674f93a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="associationset-element-csdlbi"></a>Элемент AssociationSet (CSDLBI)
  Элемент **AssociationSet** — сложный тип, который определяет взаимосвязь. В модели данных CSDLBI взаимосвязь представляет собой связь между таблицами.  
  
 Элемент **AssociationSet** должен быть задан для каждой связи в модели. Элемент **AssociationSet** определяет конечные точки с помощью элемента **Association** . Элемент **AssociationSet** также определяет метаданные о связи и их использование в модели данных.  
  
## <a name="applicable-attributes"></a>Применимые атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент **AssociationSet** .  
  
|Название|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Состояние|Да|Строка, которая указывает, активна ассоциация или нет. Значение определяется элементом State.|  
|Скрыта|Нет|Логическое значение, определяющее, является ли связь видимой. По умолчанию значение Hidden — **false**, т. е. все связи видимы в модели.|  
  
## <a name="state-element"></a>Элемент State  
 Элемент **State** — простой тип, который описывает, активна ли связь, должен использоваться в вычислениях или оставаться неактивным, но ссылаться на него в вычислениях следует явно.  
  
 Если имеется несколько наборов ассоциаций между двумя сущностями, не более одного набора ассоциаций может быть отмечено как Active. Другими словами, если между одними и теми же двумя таблицами есть две связи, то только одна связь может быть активной.  
  
 В следующей таблице перечислены значения элемента **State** .  
  
|Значение|Описание|  
|-----------|-----------------|  
|Активен|Взаимосвязь активна.|  
|Неактивный|Взаимосвязь активна.|  
  
## <a name="example"></a>Пример  
 **Табличный**  
  
 В следующем примере показана связь в табличной модели AdventureWorks для CSDLBI версии 1.1. Взаимосвязь помечена как неактивная, так как связь уже существует (между OrderKey и Date).  
  
```  
<AssociationSet   
    Name="InternetSales_Date_Date_Date"  
    Association="Sandbox.InternetSales_Date_Date_Date">  
    <End EntitySet="InternetSales" />  
    <End EntitySet="DimDate" />  
<bi:AssociationSet State="Inactive" />  
</AssociationSet>  
  
```  
  
## <a name="example"></a>Пример  
 **Multidimensional**  
  
 В следующем примере показана связь, определенная между таблицами Sales и Currency в кубе операций Contoso.  
  
```  
<AssociationSet   
    Name ="Sales_Currency_Currency_Currency_Name2"  
    Association ="Sandbox.Sales_Currency_Currency_Currency_Name2">  
    <End EntitySet ="Sales" />  
    <End EntitySet ="Currency" />  
<bi:AssociationSet />  
</AssociationSet>  
```  
  
## <a name="see-also"></a>См. также:  
 [Технический справочник по аннотациям бизнес-аналитики для языка CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
