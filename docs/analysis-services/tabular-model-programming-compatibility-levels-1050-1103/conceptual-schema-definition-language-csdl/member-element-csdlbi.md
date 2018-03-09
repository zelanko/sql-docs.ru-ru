---
title: "Элемент Member (CSDLBI) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 1ba225f5-3867-4aae-a519-e3c277688d1e
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5507e746f2f87abe2c4a08b5bda47a2eab5f61b5
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="member-element-csdlbi"></a>Элемент Member (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Элемент Member — сложный тип, который служит основой для других элементов.  
  
 Эти атрибуты могут отображаться в столбцах, мерах, свойствах навигации, иерархиях и уровнях.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент Member.  
  
|Название|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Название||Имя, присвоенное элементу (столбцу, мере, свойству навигации, иерархии или уровню), определяемое реализацией типа TMember.|  
|Заголовок|Да|Отображаемое имя элемента.|  
|ContextualNameRule|Да|Формат имени, используемый для однозначного определения элементов. Содержимое этого атрибута определяется простым типом ContextualNameRule.|  
|Скрыта||Логическое значение, которое указывает, будет ли скрыт элемент для клиента.<br /><br /> Значение по умолчанию равно FALSE, то есть столбцы отображаются в клиенте.|  
|ReferenceName||Идентификатор, используемый для ссылки на элемент в запросе DAX. Если этот атрибут отсутствует, используется имя поля|  
  
## <a name="contextualnamerule-element"></a>Элемент ContextualNameRule  
 Этот простой тип определяет формат имени, используемый для однозначного определения элементов.  
  
|Значение|Description|  
|-----------|-----------------|  
|None|Использовать имя атрибута.|  
|Контекст|Использовать имя входящей связи.|  
|Объединить|Объединить имя входящей связи и имя свойства.|  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о модели табличного объекта на совместимость уровни 1050 до 1103](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
