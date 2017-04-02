---
title: "Изменение имени атрибута и типа данных (службы Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "атрибуты [службы Master Data Services], изменение имени"
ms.assetid: d348f238-f59d-41c7-ad20-3ccd55bfd9e5
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "erikre"
caps.handback.revision: 9
---
# Изменение имени атрибута и типа данных (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно изменять имя атрибутов.  
  
## Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### Изменение имени атрибута и типа данных  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Manage Model** (Управление моделью) выберите в сетке модель и щелкните **Сущности**.  
  
3.  На странице **Управление сущностью** выберите строку сущности, для которой необходимо создать атрибут.  
  
4.  Нажмите **Атрибуты**.  
  
5.  На странице **Управление атрибутами** выполните одно из следующих действий:  
  
    -   Если атрибут предназначен для конечных элементов, в списке **Типы членов** выберите **Конечный элемент** .  
  
    -   Если атрибут предназначен для консолидированных элементов, в списке **Типы членов** выберите **Консолидированный элемент** .  
  
    -   Если атрибут предназначен для коллекций, в списке **Типы членов** выберите **Коллекция** .  
  
6.  Выберите строку для атрибута, который необходимо изменить, а затем нажмите **Изменить**.  
  
7.  Введите новое имя атрибута в поле **Имя** . Список слов, которые не должны использоваться как имена атрибутов, см. в разделе [Зарезервированные слова (службы Master Data Services)](../master-data-services/reserved-words-master-data-services.md).  
  
8.  Выберите другой тип в списке **Тип атрибута** .  
  
9. Нажмите кнопку **Сохранить**.  
  
## См. также:  
 [Создание текстового атрибута (службы Master Data Services)](../master-data-services/create-a-text-attribute-master-data-services.md)   
 [Удаление атрибута (службы Master Data Services)](../master-data-services/delete-an-attribute-master-data-services.md)   
 [Атрибуты (службы Master Data Services)](../master-data-services/attributes-master-data-services.md)  
  
  