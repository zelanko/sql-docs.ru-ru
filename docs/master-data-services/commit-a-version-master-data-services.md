---
title: "Фиксация версии (службы Master Data Services) | Microsoft Docs"
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
  - "фиксация версий [службы Master Data Services]"
  - "версии [службы Master Data Services], фиксация"
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Фиксация версии (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]фиксация версии модели препятствует изменениям элементов модели и их атрибутов. Открыть зафиксированную версию нельзя.  
  
## Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Управление версиями** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Версия должна иметь состояние **Заблокирована**. Дополнительные сведения см. в разделе [Блокировка версии (службы Master Data Services)](../master-data-services/lock-a-version-master-data-services.md).  
  
-   Все элементы должны пройти проверку.  
  
-   Необходимо иметь разрешение на доступ к функциональной области "Управление версиями". Дополнительные сведения см. в разделе [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### Фиксация версии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление версиями**.  
  
2.  На странице **Управление версиями** в строке меню щелкните **Проверить версию**.  
  
3.  На странице **Проверка версии** выберите модель и версию, которые необходимо зафиксировать.  
  
4.  Нажмите кнопку **Зафиксировать**.  
  
5.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## Следующие шаги  
  
-   [Создание флага версии (службы Master Data Services)](../master-data-services/create-a-version-flag-master-data-services.md)  
  
-   [Назначение флага версии (службы Master Data Services)](../master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
-   [Копирование версии (службы Master Data Services)](../master-data-services/copy-a-version-master-data-services.md)  
  
## См. также:  
 [Версии (службы Master Data Services)](../master-data-services/versions-master-data-services.md)  
  
  