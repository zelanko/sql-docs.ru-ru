---
title: Элемент Member (CSDLBI) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 39c8271c188d22cf6246e6c6c969b4a3d224b3e8
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
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
  
  
