---
title: Создание администратора модели (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], creating
ms.assetid: dae17afc-3b39-490e-b51f-2d8da26d429e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: bccf908359fa0cb75a8ae0bcfe7a601ccbfd6618
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65483413"
---
# <a name="create-a-model-administrator-master-data-services"></a>Создание администратора модели (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]создайте администратора модели, если требуется, чтобы группа или пользователь имели разрешение **Обновление** для всех объектов в одной или нескольких моделях.  
  
> [!TIP]  
>  Чтобы упростить администрирование, создайте локальную группу или группу Windows и настройте ее в качестве администратора модели. Впоследствии добавлять пользователей в группу и удалять их из нее можно без обращения к [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо разрешение на доступ к функциональной области **Разрешения пользователей и групп** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](administrators-master-data-services.md).  
  
### <a name="to-create-a-model-administrator"></a>Создание администратора модели  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните **Разрешения пользователей и групп**.  
  
2.  На странице **Пользователи** или **Группы** выберите строку пользователя или группы, которые необходимо изменить.  
  
3.  Нажмите **Изменить выделенного пользователя**.  
  
4.  Перейдите на вкладку **Модели** .  
  
5.  По желанию выберите модель из списка **Модель** .  
  
6.  Щелкните **Правка**.  
  
7.  Щелкните модель, разрешение на которую необходимо предоставить.  
  
8.  В меню выберите **Обновить**.  
  
9. Выполните шаги 7 и 8 для каждой модели, для которой необходимо назначить администратором пользователя или группу.  
  
10. Выберите команду **Сохранить**.  
  
## <a name="remarks"></a>Remarks  
 Не назначайте какие-либо другие разрешения объектам модели или элементам иерархий. В этом случае пользователь больше не является администратором и не может просматривать модель в любой функциональной области, отличной от **Explorer**.  
  
 Существует одно исключение: Если пользователь имеет разрешение на **Обновление** , назначенное **корню** иерархии на вкладке **элементы иерархии** , пользователь по-прежнему считается администратором модели.  
  
## <a name="see-also"></a>См. также:  
 [Администраторы &#40;Master Data Services&#41;](administrators-master-data-services.md)   
 [Назначение разрешений объекта модели &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Назначение разрешений элемента иерархии &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Разрешения объекта модели &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Разрешения элемента иерархии &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
