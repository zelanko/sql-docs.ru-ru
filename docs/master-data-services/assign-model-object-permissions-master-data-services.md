---
title: Назначение разрешения объекта модели
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], assigning object permissions
- permissions [Master Data Services], assigning model object permissions
ms.assetid: 4b80148d-2318-415c-9479-28c240e48bcd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a6c1dbc6be8ba8ddde53ea1ccdfa97fe7992a4b5
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73728737"
---
# <a name="assign-model-object-permissions-master-data-services"></a>Назначение разрешения для объекта модели (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]назначьте разрешения для объектов модели при необходимости разрешить пользователю или группе доступ к данным в функциональной области **Обозреватель** в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]или при необходимости сделать пользователя или группу администратором.  
  
> [!NOTE]  
>  При назначении разрешения на модель доступ ко всем другим моделям неявно запрещается. Если не будут назначены никакие разрешения, то пользователи и группы не смогут обращаться к данным в **Обозревателе**.  
  
## <a name="prerequisites"></a>необходимые компоненты  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Разрешения пользователей и групп** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-assign-model-object-permissions"></a>Назначения разрешений объекта модели  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните **Разрешения пользователей и групп**.  
  
2.  На странице **Пользователи** или **Группы** выберите строку пользователя или группы, которые необходимо изменить.  
  
3.  Нажмите **Изменить выделенного пользователя**.  
  
4.  Перейдите на вкладку **Модели** .  
  
5.  По желанию выберите модель из списка **Модель** .  
  
6.  Нажмите кнопку **Изменить**.  
  
7.  Разверните дерево и щелкните объект модели, для которого нужно назначить разрешения.  
  
8.  В меню выберите разрешения на создание, чтение, обновление и удаление или запретите их.  
  
9. На верхнем уровне модели выберите **Администратор** , если необходимо сделать пользователя администратором модели.  
  
10. Нажмите кнопку **Сохранить**.  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Назначение разрешений для элемента иерархии (службы Master Data Services)](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md) (необязательно)  
  
## <a name="see-also"></a>См. также статью  
 [Удаление разрешений для объекта модели (службы Master Data Services)](../master-data-services/delete-model-object-permissions-master-data-services.md)   
 [Разрешения объекта модели (службы Master Data Services)](../master-data-services/model-object-permissions-master-data-services.md)   
 [Создание администратора модели (службы Master Data Services)](../master-data-services/create-a-model-administrator-master-data-services.md)  
  
  
