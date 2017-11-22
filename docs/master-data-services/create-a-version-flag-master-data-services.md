---
title: "Создание флага версии (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating version flags [Master Data Services]
- version flags [Master Data Services], creating
- versions [Master Data Services], creating flags
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
caps.latest.revision: "7"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 478b2282dc77ac64663d843033ee5b275b8ff5b5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="create-a-version-flag-master-data-services"></a>Создание флага версии (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]флаг версии создается, чтобы назначить версию. Флаг может указывать на то, какую версию следует использовать пользователям или системам-подписчикам.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Управление версиями** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Необходимо иметь разрешение на доступ к функциональной области "Управление версиями". Дополнительные сведения см. в разделе [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### <a name="to-create-a-version-flag"></a>Создание флага версии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление версиями**.  
  
2.  На панели меню страницы **Управление версиями** наведите курсор на **Управление** и выберите **Флаги**.  
  
3.  На странице **Управление флагами версий** выберите модель в поле **Модель** , для которой нужно создать флаг.  
  
4.  Нажмите кнопку **Добавить**.  
  
5.  В поле **Имя** введите имя.  
  
6.  В поле **Описание** введите описание.  
  
7.  В поле **Только зафиксированные версии** выберите **True** , чтобы указать, что флаг может назначаться только версиям со статусом **Зафиксированная** . Выберите **False** , чтобы указать, что флаг может назначаться версиям с любым состоянием.  
  
8.  Нажмите кнопку **Сохранить**.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Назначение флага версии (службы Master Data Services)](../master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Версии (службы Master Data Services)](../master-data-services/versions-master-data-services.md)   
 [Изменение имени флага версии (службы Master Data Services)](../master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  
