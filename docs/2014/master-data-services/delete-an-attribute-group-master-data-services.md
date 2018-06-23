---
title: Удаление группы атрибутов (службы Master Data Services) | Документы Майкрософт
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
- deleting attribute groups [Master Data Services]
- attribute groups [Master Data Services], deleting
ms.assetid: f915e89b-629d-4725-aea6-a7f051978244
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: ebf2b900457a7c358c86e3df2c0abe06c69b98c2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180071"
---
# <a name="delete-an-attribute-group-master-data-services"></a>Удаление группы атрибутов (службы Master Data Services)
  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно удалить группу атрибутов, если больше не нужна вкладка для отображения в функциональной области **Обозреватель** в среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
-   **Примечание.** Если группы атрибутов существуют, то атрибуты, не принадлежащие ни к одной группе, не отображаются в окне **Обозреватель**. Если групп атрибутов не существует, то отображаются все атрибуты.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-delete-an-attribute-group"></a>Удаление группы атрибутов  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На **представление модели** страницы, в строке меню наведите курсор на **управление** и нажмите кнопку **группы атрибутов**.  
  
3.  Выберите модель из списка **Модель** .  
  
4.  Выберите сущность из списка **Сущность** .  
  
5.  Щелкните знак «плюс», чтобы развернуть **конечные группы**, **консолидированные группы**, или **группы коллекции**, в зависимости от типа группы, которые требуется удалить.  
  
6.  Щелкните группу атрибутов, которую необходимо удалить.  
  
7.  Нажмите кнопку **удалить выбранную группу**.  
  
8.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
9. В дополнительном диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Группы атрибутов &#40;службы Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md)   
 [Создание группы атрибутов &#40;службы Master Data Services&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)  
  
  