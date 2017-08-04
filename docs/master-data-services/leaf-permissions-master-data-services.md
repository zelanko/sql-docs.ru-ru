---
title: "Конечные разрешения (Master Data Services) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attribute groups [Master Data Services], permissions
- members [Master Data Services], leaf member permissions
- permissions [Master Data Services], leaf members
- leaf members [Master Data Services], attribute permissions
- attributes [Master Data Services], leaf member attribute permissions
ms.assetid: bde16e8c-bcd4-4041-8130-55c5450e5f72
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: caaea89264b37bd2c92f9c72a1cb7644b67b1fd4
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="leaf-permissions-master-data-services"></a>Разрешения конечного элемента (службы основных данных)
  Разрешения конечного элемента применяются к значениям атрибутов для всех конечных элементов сущности.  
  
 Для сущностей, у которых нет явных иерархий, назначение разрешения **Конечный** равнозначно назначению разрешения сущности.  
  
 **Примечания.**  
  
-   Разрешения конечного элемента применяются только к функциональной области **Обозреватель** пользовательского интерфейса.  
  
-   Разрешения, назначенные для атрибутов **Имя** и **Код** , не применяются.  
  
|Разрешение|Description|  
|----------------|-----------------|  
|**Чтение**|Пользователь может просматривать конечные элементы и атрибуты.|  
|**Создание**|Пользователь может создавать конечные элементы и назначать значения атрибутов во время создания.|  
|**Update**|Пользователь может обновлять конечные элементы и атрибуты.|  
|**Delete**|Пользователь может удалять конечные элементы.|  
|**Запретить**|Запрет любого доступа к конечным элементам.|  
  
 Разрешения на чтение, создание, обновление и удаление можно использовать в различных сочетаниях. Когда назначается разрешение на создание, обновление или удаление, автоматически добавляется и разрешение на чтение.  
  
## <a name="attribute-permissions"></a>Разрешения атрибута  
 Разрешения атрибута применимы только к значениям атрибута указанной сущности. Пользователи с разрешениями только для атрибутов не могут добавлять или удалять элементы.  
  
|Разрешение|Description|  
|----------------|-----------------|  
|**Чтение**|Пользователь может просматривать атрибуты.|  
|**Создание**|Пользователь может назначать значения при создании элементов.|  
|**Update**|Пользователь может обновлять атрибуты.|  
|**Delete**|Не влияет.|  
|**Запретить**|Атрибут не отображается.<br /><br /> Примечание. Нельзя явно запретить доступ к атрибутам "Имя" и "Код".|  
  
### <a name="example"></a>Пример  
 Сущности "Продукт" назначьте разрешение **Обновление** для атрибута Subcategory. Отмените разрешения для всех остальных атрибутов.  
  
|Имя|Код|Подкатегория (Обновление)|  
|----------|----------|----------------------------|  
|Mountain-100|BK-M101|{5} Горные велосипеды|  
|Mountain-100|BK-M201|{5} Горные велосипеды|  
  
 В **обозревателе**можно обновить любое значение атрибута в столбце "Subcategory". Если у пользователя нет разрешения для атрибута, атрибут не отображается.  
  
> [!NOTE]  
>  В этом примере «Подкатегория» является доменным атрибутом на основе сущности SubcategoryList. Можно выбрать другую подкатегорию для Mountain-100, но нельзя добавлять элементы или удалять элементы из сущности SubcategoryList.  
  
## <a name="see-also"></a>См. также:  
 [Назначение разрешения для объекта модели (службы Master Data Services)](../master-data-services/assign-model-object-permissions-master-data-services.md)   
    
 [Разрешения объекта модели (службы Master Data Services)](../master-data-services/model-object-permissions-master-data-services.md)   
 [Члены &#40; Службы Master Data Services &#41;](../master-data-services/members-master-data-services.md)   
 [Атрибуты &#40; Службы Master Data Services &#41;](../master-data-services/attributes-master-data-services.md)  
  
  

