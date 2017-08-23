---
title: "Атрибуты (Master Data Services) | Документы Microsoft"
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
- free-form attributes [Master Data Services]
- attributes [Master Data Services], about attributes
- attributes [Master Data Services], file attributes
- file attributes [Master Data Services]
- attributes [Master Data Services], free-form attributes
- attributes [Master Data Services]
ms.assetid: 95ecb75f-c559-41c3-933c-40ae60a4c2fd
caps.latest.revision: 13
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 55a658c7d4d0638c2dabf82ba910276f29178aa7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="attributes-master-data-services"></a>Атрибуты (службы Master Data Services)
  Атрибуты — это объекты, которые содержатся в сущностях [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Значения атрибутов описывают элементы сущности. Атрибут может использоваться для описания конечного элемента, объединенного элемента или коллекции.  
  
## <a name="how-attributes-relate-to-other-model-objects"></a>Связь атрибутов с другими объектами модели  
 Атрибут можно представить как столбец таблицы сущности. Значение атрибута — это значение, описывающее определенный элемент.  
  
 ![Службы Master Data Services сущность в виде таблицы](../master-data-services/media/mds-conc-entity-table.gif "службы Master Data Services сущность в виде таблицы")  
  
 При создании сущности, содержащей множество атрибутов, можно организовать атрибуты в группы. Дополнительные сведения см. в разделе [Группы атрибутов (службы Master Data Services)](../master-data-services/attribute-groups-master-data-services.md).  
  
## <a name="required-attributes"></a>Обязательные атрибуты  
 При создании сущности атрибуты «Имя» и «Код» создаются автоматически. Атрибут «Код» должен иметь значение, уникальное внутри сущности. Удалить атрибуты «Имя» и «Код» нельзя.  
  
## <a name="attribute-types"></a>Типы атрибутов  
 Существует три типа атрибутов.  
  
-   Атрибуты свободной формы, допускающие свободный ввод текста, чисел, дат или ссылок.  
  
-   Атрибуты на основе домена, заполненные сущностями. Дополнительные сведения см. в разделе [Атрибуты на основе домена (службы Master Data Services)](../master-data-services/domain-based-attributes-master-data-services.md).  
  
-   Файловые атрибуты, используемые для хранения файлов, документов или изображений. Атрибуты файлов помогают обеспечивать согласованность данных, требуя наличия у файла определенного расширения. Атрибуты файлов не могут гарантированно запретить злоумышленнику передать файл другого типа.  
  
### <a name="numeric-free-form-attributes"></a>Числовые атрибуты в свободной форме  
 Числовые атрибуты в свободной форме нуждаются в специальной обработке, так как они могут иметь значения только типа **SqlDouble** .  
  
 По умолчанию значение **SqlDouble** содержит 15 знаков после запятой, хотя для внутренних целей поддерживается до 17 знаков. Точность числа с плавающей запятой может иметь следующие эффекты.  
  
-   Два числа с плавающей запятой, которые могут казаться равными при определенной точности, на самом деле отличаются, поскольку их менее значащие цифры различаются.  
  
-   Математическая операция или сравнение, в которой используется число с плавающей запятой, может выдавать разные результаты при использовании десятичного числа, поскольку число с плавающей запятой может не совсем точно соответствовать десятичному числу.  
  
-   Значение может не допускать *обратного преобразования* , если представлено числом с плавающей запятой. Значение называется обратимым, если после некоторой операции, преобразующей исходное число с плавающей запятой в другой вид, и применения обратной операции, которая возвращает полученный результат обратно к числу с плавающей запятой, получившееся число равно исходному числу с плавающей запятой. Обратимость может нарушаться, если в результате преобразования теряются или меняются одна или несколько менее значащих цифр.  
  
## <a name="attribute-examples"></a>Примеры атрибутов  
 В следующем примере сущность имеет атрибуты: Name, Code, Subcategory, StandardCost, ListPrice и FilePhoto. Эти атрибуты описывают элементы. Каждый элемент представлен отдельной строкой значений атрибута.  
  
 ![Bike сущности таблицы Product](../master-data-services/media/mds-conc-entity-table-w-data.gif "велосипеда таблицы сущности продукта")  
  
 В следующем примере сущность Product содержит:  
  
-   атрибуты в свободной форме Name, Code, StandardCost и ListPrice;  
  
-   атрибут на основе домена Subcategory;  
  
-   атрибут файла FilePhoto.  
  
 Сущность Subcategory используется в качестве атрибута на основе домена сущности Product. Сущность Category используется в качестве атрибута на основе домена сущности Subcategory. Как и сущность Product, сущности Category и Subcategory по умолчанию содержат атрибуты Name и Code.  
  
 ![Древовидная структура сущности продукта](../master-data-services/media/mds-conc-entity-ui.gif "древовидная структура сущности продукта")  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание нового текстового атрибута в свободной форме.|[Создание текстового атрибута (службы Master Data Services)](../master-data-services/create-a-text-attribute-master-data-services.md)|  
|Создание нового числового атрибута в свободной форме.|[Создание числового атрибута (службы Master Data Services)](../master-data-services/create-a-numeric-attribute-master-data-services.md)|  
|Создание нового атрибута ссылки в свободной форме.|[Создание атрибута ссылки (службы Master Data Services)](../master-data-services/create-a-link-attribute-master-data-services.md)|  
|Создание нового файлового атрибута.|[Создание файлового атрибута (службы Master Data Services)](../master-data-services/create-a-file-attribute-master-data-services.md)|  
|Создание нового атрибута на основе домена.|[Создание атрибута на основе домена (службы Master Data Services)](../master-data-services/create-a-domain-based-attribute-master-data-services.md)|  
|Изменение имени существующего атрибута.|[Изменение имени атрибута и типа данных (службы Master Data Services)](../master-data-services/change-an-attribute-name-and-data-type-master-data-services.md)|  
|Добавление существующих атрибутов в группу отслеживания изменений.|[Добавление атрибутов в группу отслеживания изменений (службы Master Data Services)](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|Удаление существующего атрибута.|[Удаление атрибута (службы Master Data Services)](../master-data-services/delete-an-attribute-master-data-services.md)|  
|Изменение порядка атрибутов.|[Изменение порядка атрибутов](../master-data-services/change-the-order-of-attributes.md)|  
|Создание атрибута даты|[Создание атрибута даты (службы Master Data Services)](../master-data-services/create-a-date-attribute-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Атрибуты на основе домена (службы Master Data Services)](../master-data-services/domain-based-attributes-master-data-services.md)  
  
-   [Группы атрибутов (службы Master Data Services)](../master-data-services/attribute-groups-master-data-services.md)  
  
-   [Элементы (службы Master Data Services)](../master-data-services/members-master-data-services.md)  
  
-   [Разрешения конечного элемента (службы основных данных)](../master-data-services/leaf-permissions-master-data-services.md)
  
