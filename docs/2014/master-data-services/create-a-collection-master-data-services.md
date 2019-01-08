---
title: Создание коллекции (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating collections [Master Data Services]
- collections [Master Data Services], creating
ms.assetid: 3d4f152c-863c-4385-bca9-a9fcd0402e1f
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 1c0e899ebc7180fdfbe234c893cb364d3f9d01ee
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52782356"
---
# <a name="create-a-collection-master-data-services"></a>Создание коллекции (службы Master Data Services)
  Если нужно создать плоские списки конечных и консолидированных элементов, создайте коллекцию в среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Коллекции необязательно должны включать все элементы из сущности.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   как минимум необходимо разрешение **Обновление** на объект модели коллекции для сущности;  
  
-   Для сущности необходимо разрешить использование явных иерархий и коллекций. Дополнительные сведения см. в разделе [активация сущности для явных иерархий и коллекций &#40;службы Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).  
  
### <a name="to-create-a-collection"></a>Создание коллекции  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель в списке **Модель** .  
  
2.  Выберите версию из списка **Версия** .  
  
3.  Нажмите кнопку **Браузер**.  
  
4.  В строке меню наведите указатель на меню **Коллекции** и выберите пункт *entity_name*.  
  
5.  Нажмите кнопку **Добавить коллекцию**.  
  
6.  На вкладке **Подробные сведения** в поле **Имя** введите имя коллекции.  
  
7.  В поле **Код** введите уникальный код коллекции.  
  
8.  При необходимости в текстовом поле **Описание** введите описание коллекции.  
  
9. Нажмите кнопку **ОК**.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Добавление элементов в коллекцию (службы Master Data Services)](../../2014/master-data-services/add-members-to-a-collection-master-data-services.md)  
  
## <a name="see-also"></a>См. также  
 [Коллекции (службы Master Data Services)](../../2014/master-data-services/collections-master-data-services.md)   
 [Удаление элемента или коллекции (службы Master Data Services)](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md)   
 [Создание явной иерархии (службы Master Data Services)](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)  
  
  
