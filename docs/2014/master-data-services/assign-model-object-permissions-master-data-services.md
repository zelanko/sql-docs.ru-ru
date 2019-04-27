---
title: Назначение разрешения для объекта модели (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], assigning object permissions
- permissions [Master Data Services], assigning model object permissions
ms.assetid: 4b80148d-2318-415c-9479-28c240e48bcd
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: b064acea6aa53ccb6615b787c089cd249d4eb07d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62765927"
---
# <a name="assign-model-object-permissions-master-data-services"></a>Назначение разрешения для объекта модели (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]назначьте разрешения для объектов модели при необходимости разрешить пользователю или группе доступ к данным в функциональной области **Обозреватель** в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]или при необходимости сделать пользователя или группу администратором.  
  
> [!NOTE]  
>  При назначении разрешения на модель доступ ко всем другим моделям неявно запрещается. Если не будут назначены никакие разрешения, то пользователи и группы не смогут обращаться к данным в **Обозревателе**.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Разрешения пользователей и групп** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](administrators-master-data-services.md).  
  
### <a name="to-assign-model-object-permissions"></a>Назначения разрешений объекта модели  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните **Разрешения пользователей и групп**.  
  
2.  На странице **Пользователи** или **Группы** выберите строку пользователя или группы, которые необходимо изменить.  
  
3.  Нажмите **Изменить выделенного пользователя**.  
  
4.  Перейдите на вкладку **Модели** .  
  
5.  По желанию выберите модель из списка **Модель** .  
  
6.  Нажмите кнопку **Изменить**.  
  
7.  Разверните дерево и щелкните объект модели, для которого нужно назначить разрешения.  
  
8.  В меню выберите **только для чтения**, **обновление**, или **Deny**.  
  
9. Нажмите кнопку **Сохранить**.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Назначение разрешений для элемента иерархии (службы Master Data Services)](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) (необязательно)  
  
## <a name="see-also"></a>См. также  
 [Удаление разрешений для объекта модели (службы Master Data Services)](../../2014/master-data-services/delete-model-object-permissions-master-data-services.md)   
 [Разрешения объекта модели (службы Master Data Services)](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Создание администратора модели (службы Master Data Services)](../../2014/master-data-services/create-a-model-administrator-master-data-services.md)  
  
  
