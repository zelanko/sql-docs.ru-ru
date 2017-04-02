---
title: "Элементы (службы основных данных) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "конечные элементы [службы Master Data Services]"
  - "консолидированные элементы [службы Master Data Services]"
  - "консолидированные элементы [службы Master Data Services], о консолидированных элементах"
  - "элементы [службы Master Data Services], об элементах"
  - "конечные элементы [службы Master Data Services], о конечных элементах"
  - "элементы [службы Master Data Services]"
ms.assetid: 0fda32b9-677d-4ba2-bb28-f76f2383a30f
caps.latest.revision: 16
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 14
---
# Элементы (службы основных данных)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]элементы являются физическими основными данными. Например, элемент может быть велосипедом «Road-150» в сущности «Product» или конкретным клиентом в сущности «Customer».  
  
## Связь элементов с другими объектами модели  
 Элементы можно представить как строки в таблице. Связанные элементы содержатся в сущности, а каждый элемент определен значениями атрибутов.  
  
 В этом примере таблица представляет собой сущность, строки в таблице представляют элементы, а столбцы — атрибуты. Каждая ячейка представляет значение атрибута для определенного элемента.  
  
 ![Сущность служб Master Data Services, представленная в виде таблицы](../master-data-services/media/mds-conc-entity-table.gif "Сущность служб Master Data Services, представленная в виде таблицы")  
  
## Типы элементов  
 Существует три типа элементов: конечные элементы, консолидированные элементы и элементы коллекции.  
  
 Конечные элементы являются элементами по умолчанию в сущности.  
  
-   В производных иерархиях единственный тип элементов — конечные элементы. Конечные элементы одной сущности используются как родительские элементы для конечных элементов другой сущности.  
  
-   В явных иерархиях конечные элементы находятся на низшем уровне и не могут иметь дочерних элементов.  
  
 Консолидированные элементы существуют, только если для сущности допускаются явные иерархии и коллекции.  
  
-   Производные иерархии не содержат консолидированных элементов.  
  
-   В явных иерархиях консолидированные элементы могут быть родителями других элементов в иерархии, а также дочерними элементами.  
  
## Использование иерархии и коллекций для организации элементов  
 Иерархии и коллекции можно использовать для группировки элементов для отчетов или анализа. Дополнительные сведения см. в разделах [Иерархии (службы Master Data Services)](../master-data-services/hierarchies-master-data-services.md) и [Коллекции (службы Master Data Services)](../master-data-services/collections-master-data-services.md).  
  
## Пример элемента  
 В следующем примере каждый элемент состоит из значений атрибутов Name, Code, Subcategory, StandardCost, ListPrice и FilePhoto.  
  
 ![Таблица продукта «Велосипед»](../master-data-services/media/mds-conc-entity-table-w-data.gif "Таблица продукта «Велосипед»")  
  
## Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание нового конечного элемента.|[Создание конечного элемента (службы Master Data Services)](../master-data-services/create-a-leaf-member-master-data-services.md)|  
|Создание нового объединенного элемента.|[Создание объединенного элемента (службы Master Data Services)](../master-data-services/create-a-consolidated-member-master-data-services.md)|  
|Удаление существующего элемента или коллекции.|[Удаление элемента или коллекции (службы Master Data Services)](../master-data-services/delete-a-member-or-collection-master-data-services.md)|  
|Повторная активация удаленного элемента или коллекции.|[Повторная активация элемента или коллекции (службы Master Data Services)](../master-data-services/reactivate-a-member-or-collection-master-data-services.md)|  
|Обновление значений атрибутов элемента.|[Изменение типа атрибута (надстройка MDS для Excel)](../master-data-services/microsoft-excel-add-in/change-the-attribute-type-mds-add-in-for-excel.md)|  
|Перемещение элементов в иерархии.|[Перемещение элементов в иерархии (службы Master Data Services)](../Topic/Move%20Members%20within%20a%20Hierarchy%20\(Master%20Data%20Services\).md)|  
|Исправление конфликтов слияния|[Слияние конфликтов (Master Data Services)](../master-data-services/merge-conflicts-master-data-services.md)|  
  
## См. также  
  
-   [Общие сведения о службах Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md)  
  
-   [Сущности (службы Master Data Services)](../master-data-services/entities-master-data-services.md)  
  
-   [Атрибуты (службы Master Data Services)](../master-data-services/attributes-master-data-services.md)  
  
-   [Иерархии (службы Master Data Services)](../master-data-services/hierarchies-master-data-services.md)  
  
-   [Коллекции (службы Master Data Services)](../master-data-services/collections-master-data-services.md)  
  
-   [Разрешения конечного элемента (службы основных данных)](../master-data-services/leaf-permissions-master-data-services.md)  
  
-   [Объединенные разрешения (службы основных данных)](../Topic/Consolidated%20Permissions%20\(Master%20Data%20Services\).md)  
  
-   [Операторы фильтров (службы Master Data Services)](../master-data-services/filter-operators-master-data-services.md)  
  
  