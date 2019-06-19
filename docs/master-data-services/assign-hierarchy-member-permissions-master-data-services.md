---
title: Назначение разрешений для элемента иерархии (службы Master Data Services) | Документы Майкрософт
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
manager: craigg
ms.openlocfilehash: e7fb8a3b4e627190e4fc7eb4909f4d9bd542d8f8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65478524"
---
# <a name="assign-hierarchy-member-permissions-master-data-services"></a>Назначение разрешений для элемента иерархии (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Разрешения для элементов иерархии назначаются, чтобы дать пользователям или группам возможность просматривать данные в функциональной области **Обозреватель** [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Разрешения для элементов иерархии необязательны. Они позволяют детализировать разрешения для объектов модели в случаях, когда это необходимо.  
  
## <a name="prerequisites"></a>предварительные требования  
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
  
8.  Нажмите кнопку **Изменить**.  
  
9. Разверните дерево и щелкните узел иерархии, для которого нужно назначить разрешения.  
  
10. В меню выберите сочетание разрешений на **создание**, **чтение, обновление** и **удаление** или **запретите** их.  
  
11. Нажмите кнопку **Сохранить**.  
  
    > [!NOTE]  
    >  Разрешения для элемента иерархии вступают в силу не сразу. См. раздел [Срочное применение разрешения для элемента (службы Master Data Services)](../master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
## <a name="see-also"></a>См. также  
 [Удаление разрешений элемента иерархии (службы Master Data Services)](../master-data-services/delete-hierarchy-member-permissions-master-data-services.md)   
 [Назначение разрешения для объекта модели (службы Master Data Services)](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Разрешения на элементы иерархии (службы Master Data Services)](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
