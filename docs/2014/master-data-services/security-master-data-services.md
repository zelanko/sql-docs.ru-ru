---
title: Безопасность (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 56bc41ea-de28-4184-aa7e-99111ae55af5
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 80be0aea6705ed98fd12ea3481af59e289b94604
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65482570"
---
# <a name="security-master-data-services"></a>Безопасность (службы Master Data Services)
  Используйте систему безопасности в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], чтобы пользователи имели доступ к определенным основным данным, необходимым для их работы, и не имели доступа к данным, которые не должны быть им открыты.  
  
 Систему безопасности также можно использовать для назначения администратора конкретной модели и функциональной области (например, для предоставления разрешения на создание версии модели Customer или установки прав доступа).  
  
 
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] связана с локальными пользователями и группами или пользователями и группами домена Active Directory. Система безопасности MDS позволяет создавать разные уровни детализации при определении данных, к которым пользователь будет иметь доступ. Из-за гранулярности система безопасности может стать сложной, и необходимо будет соблюдать осторожность при использовании перекрывающихся пользователей и групп. Дополнительные сведения см. в разделе [Перекрытие разрешений пользователей и групп (службы основных данных)](overlapping-user-and-group-permissions-master-data-services.md).  
  
 Можно назначить доступ безопасности в функциональной области **Разрешения пользователей и групп** веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] или с помощью веб-службы.  
  
## <a name="types-of-users"></a>Типы пользователей  
 В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]существуют два типа пользователей:  
  
-   Те, кто имеет доступ к данным в функциональной области **Обозреватель** .  
  
-   Те, кто имеет возможность выполнения административных задач в областях, отличных от области **Обозреватель**. Эти пользователи называются [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
## <a name="how-to-set-security"></a>Настройка безопасности  
 Для предоставления пользователю или группе разрешения на доступ к данным или функциям MDS необходимо назначить:  
  
-   [Доступ к функциональным областям](../../2014/master-data-services/functional-area-permissions-master-data-services.md), который определяет, к какой из пяти функциональных областей пользовательского интерфейса имеет доступ пользователь.  
  
-   [Разрешения объекта модели](../../2014/master-data-services/model-object-permissions-master-data-services.md), которые определяют атрибуты, к которым пользователь может получить доступ, и тип доступа (чтение или обновление), который пользователь имеет с этими атрибутами.  
  
-   
  [Разрешения элементов иерархии](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)(необязательны), определяющие элементы, к которым имеет доступ пользователь, и тип доступа (чтение или изменение) к этим элементам.  
  
 При назначении разрешений для атрибутов и элементов приоритет разрешений определяется пересечением разрешений и правилами. Дополнительные сведения см. в разделе [How Permissions Are Determined &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md).  
  
 Чтобы реализовать безопасность на уровне записей, создайте иерархию для сущности и назначьте разрешения пользователей для элементов иерархии. Элементы являются записями данных.  Разрешения на элементы иерархии следует использовать только в тех случаях, когда пользователь должен иметь ограниченный доступ к определенным элементам.  
  
 На следующем рисунке показана производная иерархия для сущности стиля и разрешения элементов стилей для выбранного пользователя. Разрешения для обновления назначены элементам М {мужские} и У {унисекс}, а разрешения только для чтения назначены элементу стиля "Женские". Это означает, что пользователь может обновить записи для мужских продуктов и продуктов унисекс и записи, доступные только для чтения, для женских продуктов.  
  
 ![Разрешения на производную иерархию стилей и элементов](../../2014/master-data-services/media/style-derived-hierarchy-mds.png "Разрешения на производную иерархию стилей и элементов")  
  
 Сведения о создании иерархии см. в статьях [Создание явной иерархии &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) и [создание производной иерархии &#40;Master Data Services ](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)&#41;.  
  
 Сведения о назначении разрешений для членов см. в статье [Назначение разрешений для элементов иерархии &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
## <a name="security-in-the-add-in-for-excel"></a>Безопасность для надстройки Excel  
 Набор безопасности для веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] также применяется и для [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]. Пользователи могут просматривать и работать только с данными, на которые имеют разрешение. Администраторы выполняют административные задачи.  
  
 Единственная оговорка заключается в том, что все настройки безопасности, внесенные в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , вступают в действие в Excel только спустя 20 минут. Временной интервал определяется параметром *MdsMaximumUserInformationCacheInterval* в файле web.config. Для изменения интервала времени нужно изменить параметр и перезапустить IIS.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание пользователя, который имеет полное разрешение доступа к модели.|[Создание администратора модели &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-administrator-master-data-services.md)|  
|Добавление группы Active Directory к [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Это будет первым шагом к выдаче группе разрешения на доступ к данным в веб-приложении [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|[Добавление Master Data Services &#40;группы&#41;](../../2014/master-data-services/add-a-group-master-data-services.md)|  
|Назначение разрешения для функциональной области веб-приложения [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|[Назначение разрешений функциональной области &#40;Master Data Services&#41;](../../2014/master-data-services/assign-functional-area-permissions-master-data-services.md)|  
|Назначение разрешения для значений атрибутов путем назначения разрешения для объектов модели.|[Назначение разрешений объекта модели &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)|  
|Назначение разрешения для значений элементов путем назначения разрешений для узлов иерархии.|[Назначение разрешений элемента иерархии &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)|  
  
## <a name="see-also"></a>См. также:  
 [Администраторы &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)   
 [Пользователи и группы &#40;Master Data Services&#41;](../../2014/master-data-services/users-and-groups-master-data-services.md)   
 [Разрешения функциональной области &#40;Master Data Services&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md)   
 [Разрешения объекта модели &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Разрешения элемента иерархии &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Как определяются разрешения &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
