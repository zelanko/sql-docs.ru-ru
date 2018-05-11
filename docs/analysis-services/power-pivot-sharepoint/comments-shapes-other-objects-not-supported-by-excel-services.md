---
title: Комментарии, фигуры, другие объекты, не поддерживается службами Excel Services | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cdf03b295f8f843190e3eec9583c4bd904df9d42
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="comments-shapes-other-objects-not-supported-by-excel-services"></a>Комментарии, фигуры, другие объекты, не поддерживается службами Excel
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Эта ошибка происходит, когда вы добавляете срезы в книгу [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] из списка полей [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Область применения|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint|  
|Номер версии продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Excel Web Access не может обработать объект "Фигура", который используется для управления расположением и форматированием срезов, добавленных в книгу из списка полей [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .|  
|Текст сообщения|Следующие объекты не поддерживаются службой Excel Services и могут не отображаться совсем или отображаться лишь частично:<br /><br /> комментарии, фигуры или другие объекты.<br /><br /> Некоторые функции, например запросы внешних данных, отображают данные из кэша, которые можно обновить только в Microsoft Excel.|  
  
## <a name="explanation"></a>Объяснение  
 Excel Web Access отображает эту ошибку при открытии книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в браузере и нажатии кнопки **Сведения** для сообщения **Неподдерживаемые функции. Эта книга может отображаться ненадлежащим образом**.  
  
 Эта ошибка возникает потому, что книга [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] содержит срезы, параметры которых управляются скрытым объектом "Фигура" в Excel. Объект «Фигура» отвечает за форматирование и расположение срезов по горизонтали и вертикали.  
  
 Служба Excel Services не может обработать объект «Фигура» для отображения, но, поскольку объект является скрытым, тот факт, что он не отображается, не является проблемой.  
  
## <a name="user-action"></a>Действие пользователя  
 Эту ошибку можно пропускать. Нажмите кнопку **ОК** , чтобы закрыть сообщение об ошибке и продолжить использовать книгу и срезы без проблем.  
  
  
