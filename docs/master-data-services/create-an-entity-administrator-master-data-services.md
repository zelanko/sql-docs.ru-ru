---
title: Создание администратора сущностей
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 717be1e8-488e-4219-8d1e-ca9084b864cd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bca3fbbfe08969f27c26ab0ca6a66e76468acdc8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729534"
---
# <a name="create-an-entity-administrator-master-data-services"></a>Создание администратора сущностей (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]администратор сущностей создается, когда нужно предоставить группе или пользователю все разрешения на доступ ко всем объектам в одной или нескольких сущностях либо разрешение на утверждение ожидающих наборов изменений.  
  
> [!TIP]  
>  Чтобы упростить администрирование, создайте локальную группу или группу Windows и настройте ее в качестве администратора сущностей. Впоследствии добавлять пользователей в группу и удалять их из нее можно без обращения к [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо разрешение на доступ к функциональной области **Разрешения пользователей и групп** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
## <a name="to-create-an-entity-administrator"></a>Создание администратора сущностей  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните **Разрешения пользователей и групп**.  
  
2.  Выберите строку пользователя или группы, которую необходимо изменить, а затем нажмите **Изменить выбранного пользователя**.  
  
3.  Перейдите на вкладку **Модели** , при необходимости выберите модель из списка **Модели** , после чего нажмите кнопку **Изменить**.  
  
4.  Выберите сущность, для которой необходимо предоставить разрешения, и щелкните пункт **Администратор** в меню.  
  
5.  Выполните шаг 4 для каждой сущности, для которой необходимо назначить администратором пользователя или группу.  
  
6.  Выберите команду **Сохранить**.  
  
## <a name="see-also"></a>См. также:  
 [Администраторы &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)   
 [Назначение разрешений объекта модели &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Назначение разрешений элемента иерархии &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Разрешения объекта модели &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Разрешения элемента иерархии &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
