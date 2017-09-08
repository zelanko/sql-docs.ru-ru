---
title: "Определение связей атрибутов | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
ms.assetid: 9184d344-e96d-4025-ad6f-3f75129746df
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a1b74894ea54989ca409c860f8cd95126941e118
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="attribute-relationships---define"></a>Связи - атрибутов определяют
  В службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]атрибуты играют роль строительных блоков, из которых создается измерение. Измерение содержит набор атрибутов, организованных на основе связей между ними.  
  
 Для каждой таблицы, содержащейся в измерении, существует связь атрибутов, задающая связь ключевого атрибута таблицы с другими атрибутами из той же таблицы. Эта связь устанавливается при создании измерения.  
  
 Связь атрибутов дает следующие преимущества:  
  
-   Снижает объем памяти, необходимый для обработки измерения. Это ускоряет обработку измерений, секций и запросов.  
  
-   Повышает производительность запросов, поскольку ускоряется доступ к хранилищу и лучше оптимизируются планы выполнения.  
  
-   Приводит к выбору более эффективных алгоритмов создания статистических схем (при условии, что пользовательские иерархии были определены по путям связей).  
  
    > [!NOTE]  
    >  Дополнительные сведения о важности и последствиях определения и настройки связи атрибутов см. в разделе "Увеличение производительности запросов" в [Руководстве по производительности служб SQL Server 2005 Analysis Services](http://go.microsoft.com/fwlink/?LinkId=81621).  
  
## <a name="attribute-relationship-considerations"></a>Сведения о связях атрибутов  
 Если базовые данные позволяют, следует задавать уникальную связь между атрибутами. Для задания уникальных связей между атрибутами используется вкладка **Связи атрибутов** конструктора измерений.  
  
 Любой атрибут с исходящей связью должен иметь уникальный ключ для связанного с ним атрибута. Иными словами, элемент исходного атрибута должен однозначно задавать элемент в связанном с ним атрибуте. Рассмотрим для примера связь «Город» -> «Страна». В этой связи «Город» является исходным атрибутом, а «Страна» — связанным с ним. Исходный атрибут находится на стороне «много», а связанный с ним — на стороне «один» отношения «многие к одному». Ключом для исходного атрибута будет «Город»+«Страна». Дополнительные сведения см. в разделе [Создание, изменение или удаление связи атрибутов](../../analysis-services/multidimensional-models/attribute-relationships-create-modify-or-delete-relationship.md).  
  
 Дополнительные сведения о свойствах связей атрибутов см. в разделе [Настройка свойств связи атрибутов](../../analysis-services/multidimensional-models/attribute-relationships-configure-attribute-properties.md).  
  
> [!NOTE]  
>  Если неправильно задать связь, запрос может дать неправильные результаты.  
  
## <a name="see-also"></a>См. также  
 [Связи атрибутов](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
  
  
