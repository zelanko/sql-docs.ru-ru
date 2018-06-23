---
title: Создание группы атрибутов (службы Master Data Services) | Документы Майкрософт
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
- attribute groups [Master Data Services], creating
- creating attribute groups [Master Data Services]
ms.assetid: 798c325e-e8d8-412a-b02e-118f2741d1c7
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0a063af91090ff2e8d5eb1145bb5968573d04523
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189343"
---
# <a name="create-an-attribute-group-master-data-services"></a>Создание группы атрибутов (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]группы атрибутов создаются, когда нужно отобразить атрибуты на отдельных вкладках сетки **обозревателя** .  
  
> [!NOTE]  
>  При создании группы атрибутов она автоматически скрыта от всех пользователей, кроме того, кто ее создал. Дополнительные сведения о назначении видимости группе см. в разделе [Make an Attribute Group Visible to Users &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md).  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
-   Требуется хотя бы один атрибут. Дополнительные сведения см. в разделе [Создание текстового атрибута (службы Master Data Services)](../../2014/master-data-services/create-a-text-attribute-master-data-services.md).  
  
### <a name="to-create-an-attribute-group"></a>Создание группы атрибутов  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На **представление модели** страницы, в строке меню наведите курсор на **управление** и нажмите кнопку **группы атрибутов**.  
  
3.  Выберите модель из списка **Модель** .  
  
4.  Выберите сущность из списка **Сущность** .  
  
5.  Выберите **Конечные группы**, **Консолидированные группы**или **Группы коллекций** , чтобы создать группу атрибутов для конечных элементов, объединенных элементов или коллекций соответственно.  
  
6.  Нажмите кнопку **добавить группу атрибутов**.  
  
7.  В **имя конечной группы** введите имя для группы. Это имя, отображаемое в вкладке **Explorer**.  
  
    > [!NOTE]  
    >  Если вы выбрали **консолидированные группы** или **группы коллекции** на шаге 5, это поле не является **имя объединенной группы** или **имя группы коллекции**соответственно.  
  
8.  Нажмите кнопку **Сохранить группу**.  
  
9. Разверните папку группы.  
  
10. Нажмите **Атрибуты**.  
  
11. Нажмите кнопку **изменить выбранный элемент**.  
  
12. Выберите атрибуты в **доступно** и нажмите кнопку **добавить** стрелка. Чтобы добавить все, щелкните стрелку **Добавить все** .  
  
13. При необходимости щелкните **копирование** и **работу** стрелки, чтобы изменить порядок атрибутов слева направо.  
  
14. Нажмите кнопку **Сохранить**.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Превращение группы атрибутов в видимую для пользователей &#40;службы Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md)  
  
## <a name="see-also"></a>См. также  
 [Группы атрибутов &#40;службы Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md)   
 [Атрибуты &#40;службы Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)   
 [Изменение имени группы атрибутов (службы Master Data Services)](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md)   
 [Удаление группы атрибутов (службы Master Data Services)](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md)   
 [Конечные разрешения &#40;службы Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [Консолидированные разрешения &#40;службы Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  