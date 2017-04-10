---
title: "Безопасность (службы Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56bc41ea-de28-4184-aa7e-99111ae55af5
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# Безопасность (службы Master Data Services)
  Используйте систему безопасности в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], чтобы пользователи имели доступ к определенным основным данным, необходимым для их работы, и не имели доступа к данным, которые не должны быть им открыты.  
  
 Систему безопасности также можно использовать для назначения администратора конкретной модели и функциональной области (например, для предоставления разрешения на создание версии модели Customer или установки прав доступа).  
  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] связана с локальными пользователями и группами или пользователями и группами домена Active Directory. Система безопасности MDS позволяет создавать разные уровни детализации при определении данных, к которым пользователь будет иметь доступ. Из-за гранулярности система безопасности может стать сложной, и необходимо будет соблюдать осторожность при использовании перекрывающихся пользователей и групп. Дополнительные сведения см. в разделе [Перекрытие разрешений пользователей и групп (службы основных данных)](../master-data-services/overlapping-user-and-group-permissions-master-data-services.md).  
  
 Можно назначить доступ безопасности в функциональной области **Разрешения пользователей и групп** веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] или с помощью веб-службы.  
  
## Типы пользователей  
 В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]существуют два типа пользователей:  
  
-   Те, кто имеет доступ к данным в функциональной области **Обозреватель** .  
  
-   Те, кто имеет возможность выполнения административных задач в областях, отличных от области **Обозреватель**. Эти пользователи называются [администраторами (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
## Настройка безопасности  
 Для предоставления пользователю или группе разрешения на доступ к данным или функциям MDS необходимо назначить:  
  
-   [Доступ к функциональным областям](../master-data-services/functional-area-permissions-master-data-services.md), определяющий к какой из пяти функциональных областей пользовательского интерфейса пользователь имеет доступ.  
  
-   [Разрешения объекта модели](../master-data-services/model-object-permissions-master-data-services.md), определяющие атрибуты, к которым имеет доступ пользователь, и тип доступа (чтение, создание и изменение) к этим атрибутам. Пользователь также может назначить разрешения администратора на уровне модели.  
  
-   [Разрешения элементов иерархии](../master-data-services/hierarchy-member-permissions-master-data-services.md) (необязательны), определяющие элементы, к которым имеет доступ пользователь, и тип доступа (чтение, изменение и удаление) к этим элементам.  
  
 При назначении разрешений для атрибутов и элементов приоритет разрешений определяется пересечением разрешений и правилами. Дополнительные сведения см. в разделе [Способ определения разрешений (службы Master Data Services)](../master-data-services/how-permissions-are-determined-master-data-services.md).  
  
## Безопасность для надстройки Excel  
 Набор безопасности для веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] также применяется и для [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]. Пользователи могут просматривать и работать только с данными, на которые имеют разрешение. Администраторы выполняют административные задачи.  
  
 Единственная оговорка заключается в том, что все настройки безопасности, внесенные в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , вступают в действие в Excel только спустя 20 минут. Временной интервал определяется параметром *MdsMaximumUserInformationCacheInterval* в файле web.config. Для изменения интервала времени нужно изменить параметр и перезапустить IIS.  
  
## Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание пользователя, который имеет полное разрешение доступа к модели.|[Создание администратора модели (службы Master Data Services)](../master-data-services/create-a-model-administrator-master-data-services.md)|  
|Добавление группы Active Directory к [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Это будет первым шагом к выдаче группе разрешения на доступ к данным в веб-приложении [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|[Добавление группы (службы Master Data Services)](../master-data-services/add-a-group-master-data-services.md)|  
|Назначение разрешения для функциональной области веб-приложения [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|[Назначение разрешений для функциональной области (службы Master Data Services)](../master-data-services/assign-functional-area-permissions-master-data-services.md)|  
|Назначение разрешения для значений атрибутов путем назначения разрешения для объектов модели.|[Назначение разрешения для объекта модели (службы Master Data Services)](../master-data-services/assign-model-object-permissions-master-data-services.md)|  
|Назначение разрешения для значений элементов путем назначения разрешений для узлов иерархии.|[Назначение разрешений для элемента иерархии (службы Master Data Services)](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)|  
  
## См. также:  
 [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md)   
 [Пользователи и группы (службы Master Data Services)](../master-data-services/users-and-groups-master-data-services.md)   
 [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md)   
 [Разрешения объекта модели (службы Master Data Services)](../master-data-services/model-object-permissions-master-data-services.md)   
 [Разрешения на элементы иерархии (службы Master Data Services)](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Способ определения разрешений (службы Master Data Services)](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  