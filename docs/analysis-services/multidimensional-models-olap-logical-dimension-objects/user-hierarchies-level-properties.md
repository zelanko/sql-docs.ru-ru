---
title: "Свойства - пользовательские иерархии уровня | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
helpviewer_keywords:
- user hierarchies [Analysis Services]
- hierarchies [Analysis Services], user
ms.assetid: dabb7335-887b-442a-b67c-4901ba1242b7
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: db94622cfc84d97cb6f8e7578421f4933a63af94
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
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
  
  
