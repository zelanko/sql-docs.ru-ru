---
title: Свойства - пользовательские иерархии уровня | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f9d6cc848a772f290a6222bce2906228efdae6de
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="user-hierarchies---level-properties"></a>Пользовательские иерархии - свойства уровня
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В следующей таблице приведен список и описание свойств уровня в пользовательской иерархии.  
  
|property|Описание|  
|--------------|-----------------|  
|Описание|Содержит описание уровня.|  
|HideMemberIf|Указывает, необходимо ли и когда необходимо скрывать элемент уровня от клиентских приложений. Это свойство может иметь следующие значения:<br /><br /> Никогда<br /> Элементы никогда не скрываются. Это значение по умолчанию.<br /><br /> OnlyChildWithNoName<br /> Элемент скрывается, когда он является единственным дочерним элементом своего родительского элемента и его имя пусто.<br /><br /> OnlyChildWithParentName<br /> Элемент скрывается, когда он является единственным дочерним элементом своего родительского элемента и его имя идентично имени родительского элемента.<br /><br /> NoName<br /> Элемент скрывается, когда его имя пусто.<br /><br /> ParentName<br /> Элемент скрывается, когда его имя идентично имени родительского элемента.|  
|Идентификатор|Содержит уникальный идентификатор уровня.|  
|Название|Содержит понятное имя уровня. По умолчанию имя уровня совпадает с именем исходного атрибута.|  
|SourceAttribute|Содержит имя исходного атрибута, на котором основан уровень.|  
  
## <a name="see-also"></a>См. также  
 [Свойства пользовательской иерархии](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)  
  
  
