---
title: "Разрешения конечного элемента (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
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
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3a59acad5d9eb7e24aa8fa33a9c6633ddc52f0a1
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
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
|**Удаление**|Пользователь может удалять конечные элементы.|  
|**Запретить**|Запрет любого доступа к конечным элементам.|  
  
 Разрешения на чтение, создание, обновление и удаление можно использовать в различных сочетаниях. Когда назначается разрешение на создание, обновление или удаление, автоматически добавляется и разрешение на чтение.  
  
## <a name="attribute-permissions"></a>Разрешения атрибута  
 Разрешения атрибута применимы только к значениям атрибута указанной сущности. Пользователи с разрешениями только для атрибутов не могут добавлять или удалять элементы.  
  
|Разрешение|Description|  
|----------------|-----------------|  
|**Чтение**|Пользователь может просматривать атрибуты.|  
|**Создание**|Пользователь может назначать значения при создании элементов.|  
|**Update**|Пользователь может обновлять атрибуты.|  
|**Удаление**|Не влияет.|  
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
 [Элементы (службы Master Data Services)](../master-data-services/members-master-data-services.md)   
 [Атрибуты (службы Master Data Services)](../master-data-services/attributes-master-data-services.md)  
  
  
