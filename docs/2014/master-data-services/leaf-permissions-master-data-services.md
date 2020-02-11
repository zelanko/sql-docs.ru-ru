---
title: Разрешения конечного элемента (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], permissions
- members [Master Data Services], leaf member permissions
- permissions [Master Data Services], leaf members
- leaf members [Master Data Services], attribute permissions
- attributes [Master Data Services], leaf member attribute permissions
ms.assetid: bde16e8c-bcd4-4041-8130-55c5450e5f72
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ee587881b95821c2ae23580b54d298fa496cec15
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65479171"
---
# <a name="leaf-permissions-master-data-services"></a>Разрешения конечного элемента (службы основных данных)
  Разрешения конечного элемента применяются к значениям атрибутов для всех конечных элементов сущности.  
  
 Для сущностей, у которых нет явных иерархий, назначение разрешения **Конечный** равнозначно назначению разрешения сущности.  
  
 **Заметки о**  
  
-   Разрешения конечного элемента применяются только к функциональной области **Обозреватель** пользовательского интерфейса.  
  
-   Разрешения, назначенные для атрибутов **Имя** и **Код** , не применяются.  
  
|Разрешение|Description|  
|----------------|-----------------|  
|**Только для чтения**|Конечные элементы отображаются, но пользователь не может добавлять, удалять или изменять их.<br /><br /> Если имеются консолидированные элементы, имена и коды отображаются, но пользователь не может добавлять, удалять или изменять их.|  
|**Обновляют**|Конечные элементы отображаются, и пользователь может добавлять, удалять и изменять их.<br /><br /> Если имеются консолидированные элементы, имена и коды отображаются, но пользователь не может добавлять, удалять или изменять их.|  
|**Запретить**|Конечные элементы для сущности не отображаются.|  
  
## <a name="attribute-permissions"></a>Разрешения атрибута  
 Разрешения атрибута применимы только к значениям атрибута указанной сущности. Пользователи с разрешениями только для атрибутов не могут добавлять или удалять элементы.  
  
|Разрешение|Description|  
|----------------|-----------------|  
|**Только для чтения**|Атрибут отображается, но пользователь не может изменить его значений.|  
|**Обновляют**|Атрибут отображается, и пользователь может изменить его значения.|  
|**Запретить**|Атрибут не отображается.<br /><br /> Примечание. Нельзя явно запретить доступ к атрибутам "Имя" и "Код".|  
  
### <a name="example"></a>Пример  
 Сущности "Продукт" назначьте разрешение **Обновление** для атрибута Subcategory. Отмените разрешения для всех остальных атрибутов.  
  
|Имя|Код|Подкатегория (Обновление)|  
|----------|----------|----------------------------|  
|Mountain-100|BK-M101|
  {5} Mountain Bikes|  
|Mountain-100|BK-M201|
  {5} Mountain Bikes|  
  
 В **обозревателе**можно обновить любое значение атрибута в столбце "Subcategory". Если у пользователя нет разрешения для атрибута, атрибут не отображается.  
  
> [!NOTE]  
>  В этом примере «Подкатегория» является доменным атрибутом на основе сущности SubcategoryList. Можно выбрать другую подкатегорию для Mountain-100, но нельзя добавлять элементы или удалять элементы из сущности SubcategoryList.  
  
## <a name="see-also"></a>См. также:  
 [Назначение разрешений объекта модели &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md)   
 [Объединенные разрешения &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)   
 [Разрешения объекта модели &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Master Data Services &#40;членов&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Master Data Services &#40;атрибутов&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
