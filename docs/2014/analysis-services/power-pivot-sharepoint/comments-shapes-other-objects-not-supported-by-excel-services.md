---
title: 'Следующие функции не поддерживаются службами Excel и могут не отображаться или отображаться лишь частично: комментарии, фигуры или другие объекты | Документы Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
caps.latest.revision: 4
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: de9ce6b0d7123cf2156483e6357cef25609ba4fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110053"
---
# <a name="the-following-features-are-not-supported-by-excel-services-and-may-not-display-or-may-display-only-partially-comments-shapes-or-other-objects"></a>Следующие объекты не поддерживаются службой Excel Services и могут не отображаться совсем или отображаться лишь частично: комментарии, фигуры или другие объекты.
  Эта ошибка возникает при добавлении в книгу PowerPivot срезов из списка полей PowerPivot.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Область применения|PowerPivot для SharePoint|  
|Номер версии продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Веб-служба доступа Excel не может обработать объект «Фигура», который используется для управления расположением и форматированием срезов, добавленных в книгу из списка полей PowerPivot.|  
|Текст сообщения|Следующие объекты не поддерживаются службой Excel Services и могут не отображаться совсем или отображаться лишь частично:<br /><br /> комментарии, фигуры или другие объекты.<br /><br /> Некоторые функции, например запросы внешних данных, отображают данные из кэша, которые можно обновить только в Microsoft Excel.|  
  
## <a name="explanation"></a>Объяснение  
 Веб-клиент Excel отображает эту ошибку при открытии книги PowerPivot в браузере и нажатии кнопки **сведения** кнопки в окне сообщения **неподдерживаемые компоненты: Эта книга может отображаться должным образом**.  
  
 Эта ошибка возникает потому, что книга PowerPivot содержит срезы, параметры которых управляются скрытым объектом «Фигура» в Excel. Объект «Фигура» отвечает за форматирование и расположение срезов по горизонтали и вертикали.  
  
 Служба Excel Services не может обработать объект «Фигура» для отображения, но, поскольку объект является скрытым, тот факт, что он не отображается, не является проблемой.  
  
## <a name="user-action"></a>Действие пользователя  
 Эту ошибку можно пропускать. Нажмите кнопку **ОК** , чтобы закрыть сообщение об ошибке и продолжить использовать книгу и срезы без проблем.  
  
  