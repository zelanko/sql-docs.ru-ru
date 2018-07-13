---
title: Превращение группы атрибутов в видимую для пользователей (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b2f6cc27-dbc9-4f3f-961e-e81e76375248
caps.latest.revision: 3
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 94507eb6cae0db3206a02b43062871140d5f21c7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37223646"
---
# <a name="make-an-attribute-group-visible-to-users-master-data-services"></a>Превращение группы атрибутов в видимую для пользователей (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]сделайте группу атрибутов видимой для пользователей или групп, если необходимо, чтобы у пользователей присутствовали вкладки над сеткой в функциональной области **Обозреватель** .  
  
 При создании группы атрибутов она автоматически скрыта от всех пользователей, кроме того, кто ее создал.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Должна существовать хотя бы одна группа атрибутов. Дополнительные сведения см. в статье [Create an Attribute Group &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md).  
  
### <a name="to-make-an-attribute-group-visible-to-users"></a>Превращение группы атрибутов в видимую для пользователей  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На **представление модели** страницы, на панели меню наведите указатель мыши на **управление** и нажмите кнопку **группы атрибутов**.  
  
3.  Выберите модель из списка **Модель** .  
  
4.  Выберите сущность из списка **Сущность** .  
  
5.  Щелкните знак «плюс», чтобы развернуть **конечные группы**, **консолидированные группы**, или **группы коллекций**в зависимости от типа группы, вам нужно сделать видимой.  
  
6.  Щелкните значок «плюс», чтобы развернуть группу, которую нужно сделать видимой.  
  
7.  Выберите либо **пользователей** или **группы**зависимости от того, чтобы сделать группу видимой для пользователя или группу.  
  
8.  Нажмите кнопку **изменить выбранный элемент**.  
  
9. Выберите пользователей или группы в **доступно** поле и нажмите кнопку **добавить** стрелку. Чтобы добавить все, щелкните стрелку **Добавить все** .  
  
10. Нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также  
 [Группы атрибутов &#40;службы Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md)   
 [Создание группы атрибутов &#40;службы Master Data Services&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)  
  
  
