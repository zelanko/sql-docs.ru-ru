---
title: "Копирование версии (службы Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "версии [службы Master Data Services], копирование"
  - "копирование версий [службы Master Data Services]"
ms.assetid: f4678a02-bbe9-4f21-9e32-627eae053fe7
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Копирование версии (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]копирование версии модели позволяет создать из нее новую версию.  
  
## Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Управление версиями** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Необходимо иметь разрешение на доступ к функциональной области "Управление версиями". Дополнительные сведения см. в разделе [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### Копирование версии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление версиями**.  
  
2.  На странице **Управление версиями** выберите строку версии, которую необходимо скопировать.  
  
    > [!NOTE]  
    >  В зависимости от параметров [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]копирование может быть разрешено только для версий с состоянием **Зафиксирована** . Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../master-data-services/system-settings-master-data-services.md).  
  
3.  Нажмите кнопку **Копировать**.  
  
4.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## Следующие шаги  
  
-   [Изменение имени версии (службы Master Data Services)](../master-data-services/change-a-version-name-master-data-services.md)  
  
## См. также:  
 [Версии (службы Master Data Services)](../master-data-services/versions-master-data-services.md)  
  
  