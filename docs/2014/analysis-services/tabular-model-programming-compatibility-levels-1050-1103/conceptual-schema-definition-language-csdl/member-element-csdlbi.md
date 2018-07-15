---
title: Элемент Member (CSDLBI) | Документация Майкрософт
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
ms.assetid: 1ba225f5-3867-4aae-a519-e3c277688d1e
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4508dcf3e0dd590aaa92041d3a2136589b98e07d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37207944"
---
# <a name="member-element-csdlbi"></a>Элемент Member (CSDLBI)
  Элемент Member — сложный тип, который служит основой для других элементов.  
  
 Эти атрибуты могут отображаться в столбцах, мерах, свойствах навигации, иерархиях и уровнях.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент Member.  
  
|Имя|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Имя||Имя, присвоенное элементу (столбцу, мере, свойству навигации, иерархии или уровню), определяемое реализацией типа TMember.|  
|Заголовок|Да|Отображаемое имя элемента.|  
|ContextualNameRule|Да|Формат имени, используемый для однозначного определения элементов. Содержимое этого атрибута определяется простым типом ContextualNameRule.|  
|Скрытый||Логическое значение, которое указывает, будет ли скрыт элемент для клиента.<br /><br /> Значение по умолчанию равно FALSE, то есть столбцы отображаются в клиенте.|  
|ReferenceName||Идентификатор, используемый для ссылки на элемент в запросе DAX. Если этот атрибут отсутствует, используется имя поля|  
  
## <a name="contextualnamerule-element"></a>Элемент ContextualNameRule  
 Этот простой тип определяет формат имени, используемый для однозначного определения элементов.  
  
|Значение|Описание|  
|-----------|-----------------|  
|None|Использовать имя атрибута.|  
|Контекст|Использовать имя входящей связи.|  
|Объединить|Объединить имя входящей связи и имя свойства.|  
  
## <a name="see-also"></a>См. также  
 [Основные сведения о табличной объектной модели](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
