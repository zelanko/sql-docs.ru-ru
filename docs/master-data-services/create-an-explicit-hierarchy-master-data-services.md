---
title: "Создание явной иерархии (службы Master Data Services) | Microsoft Docs"
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
  - "создание явных иерархий [службы Master Data Services]"
  - "явные иерархии, создание"
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# Создание явной иерархии (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] явные иерархии создаются, если необходима неоднородная иерархия, элементы которой могут располагаться на любом уровне. Явные иерархии содержат элементы из одной сущности.  
  
 После создания явной иерархии в нее можно добавлять элементы в функциональной области **Обозреватель**.  
  
## Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Для сущности необходимо разрешить использование явных иерархий и коллекций.  
  
### Создание явной иерархии  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Manage Model** (Управление моделью) выберите в сетке модель и щелкните **Сущности**.  
  
3.  На странице **Manage Entity** (Управление сущностью) выберите в сетке строку сущности, для которой необходимо создать явную иерархию.  
  
4.  Щелкните **Явные иерархии**.  
  
5.  На странице **Manage Explicit Hierarchy** (Управление явной иерархией) нажмите **Добавить**.  
  
6.  Введите имя иерархии в поле **Имя**.  
  
7.  По желанию снимите флажок **Обязательная иерархия** для создания необязательной иерархии. Дополнительные сведения о типах иерархий см. в разделе [Явные иерархии (службы Master Data Services)](../master-data-services/explicit-hierarchies-master-data-services.md).  
  
8.  Нажмите кнопку **Сохранить**.  
  
## Столбцы сетки  
 Для каждой создаваемой явной иерархии в сетке создается строка с семью столбцами. Ниже приведено описание этих столбцов.  
  
|Название|Description|  
|----------|-----------------|  
|Состояние|Состояние сущности. После нажатия кнопки **Сохранить** появится следующее изображение, которое указывает на то, что сущность обновляется.<br /><br /> ![Icon for updating status](../master-data-services/media/mds-statusicon-updating.png "Icon for updating status")<br /><br /> При наличии ошибок во время создания или изменения сущности появляется следующее изображение.<br /><br /> ![Icon for error status](../master-data-services/media/mds-statusicon-error.png "Icon for error status")<br /><br /> Если ее состояние нормальное, появится следующее изображение.<br /><br /> ![Icon for OK status](../master-data-services/media/mds-statusicon-ok.png "Icon for OK status")|  
|Название|Имя явной иерархии.|  
|Обязательно|Указывает, является ли явная иерархия обязательной.|  
|Автор|Имя пользователя, создавшего явную иерархию.|  
|Создано|Дата и время создания явной иерархии.|  
|Кем обновлено|Имя последнего пользователя, обновившего явную иерархию.|  
|Когда обновлено|Дата и время последнего обновления явной иерархии.|  
  
## Следующие шаги  
  
-   [Создание объединенного элемента (службы Master Data Services)](../master-data-services/create-a-consolidated-member-master-data-services.md)  
  
-   [Перемещение элементов в иерархии (службы Master Data Services)](../Topic/Move%20Members%20within%20a%20Hierarchy%20\(Master%20Data%20Services\).md)  
  
## См. также:  
 [Явные иерархии (службы Master Data Services)](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [Производные иерархии с явными ограничениями (службы Master Data Services)](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Изменение имени явной иерархии (службы Master Data Services)](../master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  