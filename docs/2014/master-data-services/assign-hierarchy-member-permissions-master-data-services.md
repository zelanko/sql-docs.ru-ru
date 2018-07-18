---
title: Назначение разрешений для элемента иерархии (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], assigning member permissions
- members [Master Data Services], assigning permissions
ms.assetid: e1b8b46a-7cd1-4a7d-9345-dd7df081e145
caps.latest.revision: 5
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: e18ee83a164659904864b84dc80fb21e7f07f463
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306000"
---
# <a name="assign-hierarchy-member-permissions-master-data-services"></a>Назначение разрешений для элемента иерархии (службы Master Data Services)
  Разрешения для элементов иерархии назначаются, чтобы дать пользователям или группам возможность просматривать данные в функциональной области **Обозреватель** [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Разрешения для элементов иерархии необязательны. Они позволяют детализировать разрешения для объектов модели в случаях, когда это необходимо.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Разрешения пользователей и групп** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-assign-hierarchy-member-permissions"></a>Назначение разрешений для элементов иерархии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните **Разрешения пользователей и групп**.  
  
2.  На странице **Пользователи** или **Группы** выберите строку пользователя или группы, которые необходимо изменить.  
  
3.  Нажмите **Изменить выделенного пользователя**.  
  
4.  Перейдите на вкладку **Элементы иерархии** .  
  
5.  Выберите модель из списка **Модель** .  
  
6.  Выберите версию из списка **Версия** .  
  
7.  Выберите иерархию из списка **Иерархия** .  
  
8.  Нажмите кнопку **Изменить**.  
  
9. Разверните дерево и щелкните узел иерархии, для которого нужно назначить разрешения.  
  
10. В меню выберите **только для чтения**, **обновление**, или **Deny**.  
  
11. Нажмите кнопку **Сохранить**.  
  
    > [!NOTE]  
    >  Разрешения для элемента иерархии вступают в силу не сразу. См. раздел [Срочное применение разрешения для элемента (службы Master Data Services)](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
## <a name="see-also"></a>См. также  
 [Удаление разрешений элемента иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/delete-hierarchy-member-permissions-master-data-services.md)   
 [Назначение разрешений объекта модели &#40;службы Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Разрешения элементов иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
