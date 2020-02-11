---
title: Назначение разрешений для элемента иерархии
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], assigning member permissions
- members [Master Data Services], assigning permissions
ms.assetid: e1b8b46a-7cd1-4a7d-9345-dd7df081e145
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9a725ec385d72ea3719e215ea9b01c1565aadecc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729773"
---
# <a name="assign-hierarchy-member-permissions-master-data-services"></a>Назначение разрешений для элемента иерархии (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Разрешения для элементов иерархии назначаются, чтобы дать пользователям или группам возможность просматривать данные в функциональной области **Обозреватель**[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Разрешения для элементов иерархии необязательны. Они позволяют детализировать разрешения для объектов модели в случаях, когда это необходимо.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Разрешения пользователей и групп** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-assign-hierarchy-member-permissions"></a>Назначение разрешений для элементов иерархии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните **Разрешения пользователей и групп**.  
  
2.  На странице **Пользователи** или **Группы** выберите строку пользователя или группы, которые необходимо изменить.  
  
3.  Нажмите **Изменить выделенного пользователя**.  
  
4.  Перейдите на вкладку **Элементы иерархии** .  
  
5.  Выберите модель из списка **Модель** .  
  
6.  Выберите версию из списка **Версия** .  
  
7.  Выберите иерархию из списка **Иерархия** .  
  
8.  Щелкните **Правка**.  
  
9. Разверните дерево и щелкните узел иерархии, для которого нужно назначить разрешения.  
  
10. В меню выберите сочетание разрешений на **создание**, **чтение, обновление** и **удаление** или **запретите** их.  
  
11. Выберите команду **Сохранить**.  
  
    > [!NOTE]  
    >  Разрешения для элемента иерархии вступают в силу не сразу. См. раздел [Срочное применение разрешения для элемента (службы Master Data Services)](../master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Удаление разрешений элемента иерархии &#40;Master Data Services&#41;](../master-data-services/delete-hierarchy-member-permissions-master-data-services.md)   
 [Назначение разрешений объекта модели &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Разрешения элемента иерархии &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
