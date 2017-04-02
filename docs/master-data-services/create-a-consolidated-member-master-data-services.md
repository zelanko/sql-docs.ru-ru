---
title: "Create a Consolidated Member (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "04/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating consolidated members [Master Data Services]"
  - "members [Master Data Services], creating consolidated members"
  - "объединенные элементы [Master Data Services], создание"
ms.assetid: 431ab2d2-5517-4372-9980-142b05427c08
caps.latest.revision: 12
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 11
---
# Create a Consolidated Member (Master Data Services)
  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]объединенный элемент создается, когда нужен родительский узел для явной иерархии. Если нужно добавить данные в массовом режиме, следует использовать промежуточные таблицы. Дополнительные сведения см. в разделе [Импорт данных из таблиц (службы Master Data Services)](../master-data-services/import-data-from-tables-master-data-services.md).  
  
## Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   Как минимум, необходимо разрешение **Обновление** для объединенного объекта модели для сущности, в которую нужно добавить элемент, а также разрешение на **создание** элементов объединенного типа в этом объекте.  
  
### Создание объединенного элемента  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель в списке **Модель** .  
  
2.  Выберите версию из списка **Версия** .  
  
3.  Нажмите кнопку **Браузер**.  
  
4.  В строке меню наведите указатель мыши на **Иерархии** и щелкните имя иерархии, к которой нужно добавить объединенный элемент.  
  
5.  Над сеткой выберите вариант **Консолидированные элементы** или **Все Консолидированные элементы в иерархии** .  
  
6.  На левой панели выберите корневой узел или объединенный элемент, в котором вы хотите создать новый объединенный элемент.  
  
7.  Нажмите кнопку **Добавить**.  
  
8.  Заполните поля на панели справа.  
  
9. Необязательно. В поле **Заметки** введите комментарий о том, для чего добавлен элемент. Заметку могут просматривать все пользователи, которые имеют доступ к элементу.  
  
10. Нажмите кнопку **ОК**.  
  
## Следующие шаги  
  
-   [Перемещение элементов в иерархии (службы Master Data Services)](../Topic/Move%20Members%20within%20a%20Hierarchy%20\(Master%20Data%20Services\).md)  
  
## См. также:  
 [Создание явной иерархии (службы Master Data Services)](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [Создание конечного элемента (службы Master Data Services)](../master-data-services/create-a-leaf-member-master-data-services.md)   
 [Элементы (службы Master Data Services)](../master-data-services/members-master-data-services.md)   
 [Явные иерархии (службы Master Data Services)](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
  