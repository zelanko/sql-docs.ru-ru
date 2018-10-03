---
title: Свойства уровня | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- user hierarchies [Analysis Services]
- hierarchies [Analysis Services], user
ms.assetid: dabb7335-887b-442a-b67c-4901ba1242b7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1edce09247d89b8b87c8d03a637f84ed42e2292c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075124"
---
# <a name="level-properties"></a>Свойства уровня 
  В следующей таблице приведен список и описание свойств уровня в пользовательской иерархии.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|Описание|Содержит описание уровня.|  
|HideMemberIf|Указывает, необходимо ли и когда необходимо скрывать элемент уровня от клиентских приложений. Это свойство может иметь следующие значения:<br /><br /> Никогда<br /> Элементы никогда не скрываются. Это значение по умолчанию.<br /><br /> OnlyChildWithNoName<br /> Элемент скрывается, когда он является единственным дочерним элементом своего родительского элемента и его имя пусто.<br /><br /> OnlyChildWithParentName<br /> Элемент скрывается, когда он является единственным дочерним элементом своего родительского элемента и его имя идентично имени родительского элемента.<br /><br /> NoName<br /> Элемент скрывается, когда его имя пусто.<br /><br /> ParentName<br /> Элемент скрывается, когда его имя идентично имени родительского элемента.|  
|ID|Содержит уникальный идентификатор уровня.|  
|Имя|Содержит понятное имя уровня. По умолчанию имя уровня совпадает с именем исходного атрибута.|  
|SourceAttribute|Содержит имя исходного атрибута, на котором основан уровень.|  
  
## <a name="see-also"></a>См. также  
 [Свойства пользовательской иерархии](user-hierarchies-properties.md)  
  
  
