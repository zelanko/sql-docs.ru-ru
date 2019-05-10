---
title: Скрытие или удаление уровней в производной иерархии (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, hiding levels
- derived hierarchies, deleting levels
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d7e2dd9db5cfc9b86b1c29b165bd817ff5394798
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65483019"
---
# <a name="hide-or-delete-levels-in-a-derived-hierarchy-master-data-services"></a>Скрытие или удаление уровней в производной иерархии (службы Master Data Services)
  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно скрыть уровень в производной иерархии, если он необходим для группирования, но отображать этот уровень нежелательно. Если этот уровень не нужен для группирования, то можно удалить его.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](administrators-master-data-services.md).  
  
### <a name="to-hide-or-delete-levels-in-a-derived-hierarchy"></a>Скрытие и удаление уровней в производной иерархии  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На **представление модели** страницы, на панели меню наведите указатель мыши на **управление** и нажмите кнопку **производные иерархии**.  
  
3.  На странице **Обслуживание производной иерархии** выберите модель из списка **Модель** .  
  
4.  Выберите строку для производной иерархии, которую необходимо изменить.  
  
5.  Нажмите кнопку **изменить выбранные производную иерархию**.  
  
6.  На панели **Текущие уровни** :  
  
    -   Чтобы скрыть уровень, щелкните любой уровень (кроме верхнего и нижнего). В списке **Видимый** выберите **Нет**. Затем щелкните **Сохранить выбранный элемент иерархии**.  
  
    -   Чтобы удалить верхний уровень, щелкните **Удалить выбранный элемент иерархии**. В диалоговом окне подтверждения нажмите кнопку **ОК**. Можно удалить только верхний уровень.  
  
## <a name="see-also"></a>См. также  
 [Перемещение элементов в иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)   
 [Производные иерархии (службы Master Data Services)](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
