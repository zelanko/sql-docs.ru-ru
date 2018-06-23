---
title: Группы атрибутов (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attribute groups [Master Data Services]
- attribute groups [Master Data Services], about attribute groups
ms.assetid: 648b3d0b-e15a-45f9-8292-3a54a072e62c
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c158f4ac41d4d30cf1d53adc2ad07d10d55900fa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098433"
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
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание новой группы атрибутов и добавление к ней атрибутов.|[Создание группы атрибутов &#40;службы Master Data Services&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)|  
|Превращение группы атрибутов в видимую для пользователей|[Превращение группы атрибутов в видимую для пользователей &#40;службы Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md)|  
|Изменение имени существующей группы атрибутов.|[Изменение имени группы атрибутов &#40;службы Master Data Services&#41;](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md)|  
|Удаление существующей группы атрибутов.|[Удаление группы атрибутов &#40;службы Master Data Services&#41;](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Атрибуты &#40;службы Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  