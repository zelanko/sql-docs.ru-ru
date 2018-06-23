---
title: Создание администратора модели (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- administrators [Master Data Services], creating
ms.assetid: dae17afc-3b39-490e-b51f-2d8da26d429e
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 06f5acf3bf8c9c4f8df7282934c99b38480a1bd3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099790"
---
# <a name="create-a-model-administrator-master-data-services"></a>Создание администратора модели (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], создание администратора модели, при необходимости, группе или пользователю необходимо предоставить **обновление** разрешения на все объекты в одной или нескольких моделей.  
  
> [!TIP]  
>  Чтобы упростить администрирование, создайте локальную группу или группу Windows и настройте ее в качестве администратора модели. Впоследствии добавлять пользователей в группу и удалять их из нее можно без обращения к [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо разрешение на доступ к функциональной области **Разрешения пользователей и групп** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-a-model-administrator"></a>Создание администратора модели  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните **Разрешения пользователей и групп**.  
  
2.  На странице **Пользователи** или **Группы** выберите строку пользователя или группы, которые необходимо изменить.  
  
3.  Нажмите **Изменить выделенного пользователя**.  
  
4.  Перейдите на вкладку **Модели** .  
  
5.  По желанию выберите модель из списка **Модель** .  
  
6.  Нажмите кнопку **Изменить**.  
  
7.  Щелкните модель, разрешение на которую необходимо предоставить.  
  
8.  В меню выберите **обновление**.  
  
9. Выполните шаги 7 и 8 для каждой модели, для которой необходимо назначить администратором пользователя или группу.  
  
10. Нажмите кнопку **Сохранить**.  
  
## <a name="remarks"></a>Примечания  
 Не назначайте какие-либо другие разрешения объектам модели или элементам иерархий. В противном случае пользователь больше не является администратором и не могут просматривать модели в функциональной области отличный от **Explorer**.  
  
 Есть одно исключение: Если у пользователя есть **обновление** разрешение, назначенное для иерархии **корневой** на **элементы иерархии** , пользователь останется модели Администратор.  
  
## <a name="see-also"></a>См. также  
 [Администраторы &#40;службы Master Data Services&#41;](administrators-master-data-services.md)   
 [Назначение разрешения объекта модели &#40;службы Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Назначение разрешений для элементов иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Разрешения объекта модели &#40;службы Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Разрешения для элементов иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  