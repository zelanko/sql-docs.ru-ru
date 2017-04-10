---
title: "Обзор. Экспорт данных (службы Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "экспорт данных [службы Master Data Services]"
  - "представления подписки [службы Master Data Services]"
  - "представления подписки [службы Master Data Services], о представлениях подписки"
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
caps.latest.revision: 12
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 12
---
# Обзор. Экспорт данных (службы Master Data Services)
  В этой статье рассматриваются типы форматов представления подписки и то, как определить, когда нужно изменить представления из-за изменений в объектах модели.  
  
 Чтобы экспортировать данные служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] в системы-подписчики, например [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], нужно создать представление подписки. Система-подписчик используется для просмотра данных в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  Сведения о создании представления подписки см. в разделе [Создание представления подписки для экспорта данных (службы Master Data Services)](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)  
  
 Дополнительные сведения о представлениях см. в разделе [Представления](../relational-databases/views/views.md).  
  
## Форматы представлений подписки  
 При создании представления [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]на выбор предлагается набор стандартных форматов представлений, предоставляемых службами [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Эти форматы используются для создания представлений, которые содержат:  
  
-   все конечные элементы и их атрибуты;  
  
-   все консолидированные элементы и их атрибуты;  
  
-   все коллекции и их атрибуты;  
  
-   элементы, явно добавленные в коллекцию;  
  
-   элементы в производной иерархии многоуровневого типа или типа «родители-потомки»;  
  
-   элементы во всех явных иерархиях многоуровневого типа или типа «родители-потомки» для сущности.  
  
## Представления подписки могут устаревать  
 После создания представления подписки для сущности или иерархии изменения связанных объектов модели не будут автоматически отображаться в представлении. Может потребоваться повторное создание представления подписки в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , чтобы в ней отразились изменения в объектах модели. При изменении объектов модели значение в столбце **Изменено** на странице **Экспорт** меняется на **True** . Значение**True** указывает на необходимость изменить представление подписки и сохранить его, после чего оно будет создано повторно.  
  
## Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание представления подписки основных данных.|[Создание представления подписки для экспорта данных (службы Master Data Services)](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)|  
|Удаление существующих представлений подписки.|[Удаление представления подписки (службы Master Data Services)](../master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## См. также  
  
-   [Форматы представления подписки (Master Data Services)](../master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [Представления](../relational-databases/views/views.md)  
  
  