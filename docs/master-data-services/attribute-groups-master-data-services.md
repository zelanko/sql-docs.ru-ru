---
title: "Группы атрибутов (службы Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "группы атрибутов [службы Master Data Services]"
  - "группы атрибутов [службы Master Data Services], о группах атрибутов"
ms.assetid: 648b3d0b-e15a-45f9-8292-3a54a072e62c
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# Группы атрибутов (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]группы атрибутов помогают организовать атрибуты в сущности. Если сущность имеет множество атрибутов, то использование групп атрибутов улучшает отображение сущности в веб-приложении [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
## Изменение отображения при использовании групп атрибутов  
 Группы атрибутов отображаются как вкладки над сеткой в функциональной области **обозревателя** в веб-приложении [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Если атрибутов у сущности много и эта сущность просматривается в сетке в **Обозревателе**, то для их просмотра нужно прокручивать экран вправо. Чтобы не нужно было прокручивать экран, можно объединить атрибуты в группы.  
  
-   Группы атрибутов всегда автоматически включают атрибуты «Имя» и «Код».  
  
-   Каждый атрибут сущности может принадлежать к нескольким группам.  
  
-   Все атрибуты автоматически включаются во вкладку **Все атрибуты** в **обозревателе**.  
  
-   Нельзя скрыть вкладку **Все атрибуты** .  
  
 Управление группами атрибутов осуществляется в функциональной области **Администрирование системы** в веб-приложении [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## Отображение или скрытие групп атрибутов  
 При создании группы атрибутов она автоматически скрыта от всех пользователей, кроме того, кто ее создал. Дополнительные сведения о назначении видимости группе см. в разделе [Превращение группы атрибутов в видимую для пользователей (службы Master Data Services)](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md).  
  
 При необходимости скрыть определенный атрибут внутри группы вы можете назначить атрибуту разрешение **Запрещено** . Дополнительные сведения см. в разделе [Разрешения конечного элемента (службы основных данных)](../master-data-services/leaf-permissions-master-data-services.md) или [Объединенные разрешения (службы основных данных)](../Topic/Consolidated%20Permissions%20\(Master%20Data%20Services\).md).  
  
## Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание новой группы атрибутов и добавление к ней атрибутов.|[Создание группы атрибутов (службы Master Data Services)](../master-data-services/create-an-attribute-group-master-data-services.md)|  
|Превращение группы атрибутов в видимую для пользователей|[Превращение группы атрибутов в видимую для пользователей (службы Master Data Services)](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md)|  
|Изменение имени существующей группы атрибутов.|[Изменение имени группы атрибутов (службы Master Data Services)](../master-data-services/change-an-attribute-group-name-master-data-services.md)|  
|Удаление существующей группы атрибутов.|[Удаление группы атрибутов (службы Master Data Services)](../master-data-services/delete-an-attribute-group-master-data-services.md)|  
  
## См. также  
  
-   [Атрибуты (службы Master Data Services)](../master-data-services/attributes-master-data-services.md)  
  
  