---
description: Обзор. Экспорт данных (службы Master Data Services)
title: Exporting Data
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- exporting data [Master Data Services]
- subscription views [Master Data Services]
- subscription views [Master Data Services], about subscription views
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f477249f9f65b85598a11e40da268aa3a15b35a3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88342940"
---
# <a name="overview-exporting-data-master-data-services"></a>Обзор. Экспорт данных (службы Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  В этой статье рассматриваются типы форматов представления подписки и то, как определить, когда нужно изменить представления из-за изменений в объектах модели.  
  
 Чтобы экспортировать данные служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] в системы-подписчики, например [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], нужно создать представление подписки. Система-подписчик используется для просмотра данных в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  Сведения о создании представления подписки см. в разделе [Создание представления подписки для экспорта данных (службы Master Data Services)](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)  
  
 Дополнительные сведения о представлениях см. в разделе [Представления](../relational-databases/views/views.md).  
  
## <a name="subscription-view-formats"></a>Форматы представлений подписки  
 При создании представления [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]на выбор предлагается набор стандартных форматов представлений, предоставляемых службами [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Эти форматы используются для создания представлений, которые содержат:  
  
-   все конечные элементы и их атрибуты;  
  
-   все консолидированные элементы и их атрибуты;  
  
-   все коллекции и их атрибуты;  
  
-   элементы, явно добавленные в коллекцию;  
  
-   элементы в производной иерархии многоуровневого типа или типа «родители-потомки»;  
  
-   элементы во всех явных иерархиях многоуровневого типа или типа «родители-потомки» для сущности.  
  
## <a name="subscription-views-can-become-out-of-date"></a>Представления подписки могут устаревать  
 После создания представления подписки для сущности или иерархии изменения связанных объектов модели не будут автоматически отображаться в представлении. Может потребоваться повторное создание представления подписки в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , чтобы в ней отразились изменения в объектах модели. При изменении объектов модели значение в столбце **Изменено** на странице **Экспорт** меняется на **True** . Значение**True** указывает на необходимость изменить представление подписки и сохранить его, после чего оно будет создано повторно.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание представления подписки основных данных.|[Создание представления подписки для экспорта данных (службы Master Data Services)](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)|  
|Удаление существующих представлений подписки.|[Удаление представления подписки (службы Master Data Services)](../master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Форматы представления подписки (Master Data Services)](../master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [Представления](../relational-databases/views/views.md)  
  
  
