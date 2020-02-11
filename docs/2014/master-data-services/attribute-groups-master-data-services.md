---
title: Группы атрибутов (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services]
- attribute groups [Master Data Services], about attribute groups
ms.assetid: 648b3d0b-e15a-45f9-8292-3a54a072e62c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: bacb199a87cd0d9e388b49b00cbc2e245571d2ec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65483700"
---
# <a name="attribute-groups-master-data-services"></a>Группы атрибутов (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]группы атрибутов помогают организовать атрибуты в сущности. Если сущность имеет множество атрибутов, то использование групп атрибутов улучшает отображение сущности в веб-приложении [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
## <a name="how-attribute-groups-change-the-display"></a>Изменение отображения при использовании групп атрибутов  
 Группы атрибутов отображаются как вкладки над сеткой в функциональной области **обозревателя** в веб-приложении [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Если атрибутов у сущности много и эта сущность просматривается в сетке в **Обозревателе**, то для их просмотра нужно прокручивать экран вправо. Чтобы не нужно было прокручивать экран, можно объединить атрибуты в группы.  
  
-   Группы атрибутов всегда автоматически включают атрибуты «Имя» и «Код».  
  
-   Каждый атрибут сущности может принадлежать к нескольким группам.  
  
-   Все атрибуты автоматически включаются во вкладку **Все атрибуты** в **обозревателе**.  
  
-   Нельзя скрыть вкладку **Все атрибуты** .  
  
 Управление группами атрибутов осуществляется в функциональной области **Администрирование системы** в веб-приложении [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="show-or-hide-attribute-groups"></a>Отображение или скрытие групп атрибутов  
 При создании группы атрибутов она автоматически скрыта от всех пользователей, кроме того, кто ее создал. Дополнительные сведения о назначении видимости группе см. в разделе [Make an Attribute Group Visible to Users &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md).  
  
 При необходимости скрыть определенный атрибут внутри группы вы можете назначить атрибуту разрешение **Запрещено** . Дополнительные сведения см. в разделе [Разрешения конечного элемента (службы основных данных)](../../2014/master-data-services/leaf-permissions-master-data-services.md) или [Объединенные разрешения (службы основных данных)](../../2014/master-data-services/consolidated-permissions-master-data-services.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание новой группы атрибутов и добавление к ней атрибутов.|[Создание группы атрибутов &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)|  
|Превращение группы атрибутов в видимую для пользователей|[Сделать группу атрибутов видимой для пользователей &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md)|  
|Изменение имени существующей группы атрибутов.|[Изменение имени группы атрибутов &#40;Master Data Services&#41;](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md)|  
|Удаление существующей группы атрибутов.|[Удаление группы атрибутов &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Master Data Services &#40;атрибутов&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
