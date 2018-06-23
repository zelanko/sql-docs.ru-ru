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
ms.topic: article
ms.assetid: b2f6cc27-dbc9-4f3f-961e-e81e76375248
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 70dcc1e8f35f288b4693bd87308d7f2abcff0136
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180073"
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
  
2.  На **представление модели** страницы, в строке меню наведите курсор на **управление** и нажмите кнопку **группы атрибутов**.  
  
3.  Выберите модель из списка **Модель** .  
  
4.  Выберите сущность из списка **Сущность** .  
  
5.  Щелкните знак «плюс», чтобы развернуть **конечные группы**, **консолидированные группы**, или **группы коллекции**, в зависимости от типа группы должны быть видимыми.  
  
6.  Щелкните значок «плюс», чтобы развернуть группу, которую нужно сделать видимой.  
  
7.  Выберите либо **пользователей** или **группы**в зависимости от того, чтобы сделать группу видимой для пользователя или группы.  
  
8.  Нажмите кнопку **изменить выбранный элемент**.  
  
9. Выберите пользователей или группы в **доступно** и нажмите кнопку **добавить** стрелка. Чтобы добавить все, щелкните стрелку **Добавить все** .  
  
10. Нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также  
 [Группы атрибутов &#40;службы Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md)   
 [Создание группы атрибутов &#40;службы Master Data Services&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)  
  
  