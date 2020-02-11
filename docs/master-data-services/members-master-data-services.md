---
title: Члены
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- leaf members [Master Data Services]
- consolidated members [Master Data Services]
- consolidated members [Master Data Services], about consolidated members
- members [Master Data Services], about members
- leaf members [Master Data Services], about leaf members
- members [Master Data Services]
ms.assetid: 0fda32b9-677d-4ba2-bb28-f76f2383a30f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d6e663ef23c472b2a78ec71c58086824adae185e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728003"
---
# <a name="members-master-data-services"></a>Элементы (службы основных данных)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]элементы являются физическими основными данными. Например, элемент может быть велосипедом «Road-150» в сущности «Product» или конкретным клиентом в сущности «Customer».  
  
## <a name="how-members-relate-to-other-model-objects"></a>Связь элементов с другими объектами модели  
 Элементы можно представить как строки в таблице. Связанные элементы содержатся в сущности, а каждый элемент определен значениями атрибутов.  
  
 В этом примере таблица представляет собой сущность, строки в таблице представляют элементы, а столбцы — атрибуты. Каждая ячейка представляет значение атрибута для определенного элемента.  
  
 ![Сущность служб Master Data Services, представленная в виде таблицы](../master-data-services/media/mds-conc-entity-table.gif "Сущность служб Master Data Services, представленная в виде таблицы")  
  
## <a name="member-types"></a>Типы элементов  
 Существует три типа элементов: конечные элементы, консолидированные элементы и элементы коллекции.  
  
 Конечные элементы являются элементами по умолчанию в сущности.  
  
-   В производных иерархиях единственный тип элементов — конечные элементы. Конечные элементы одной сущности используются как родительские элементы для конечных элементов другой сущности.  
  
-   В явных иерархиях конечные элементы находятся на низшем уровне и не могут иметь дочерних элементов.  
  
 Консолидированные элементы существуют, только если для сущности допускаются явные иерархии и коллекции.  
  
-   Производные иерархии не содержат консолидированных элементов.  
  
-   В явных иерархиях консолидированные элементы могут быть родителями других элементов в иерархии, а также дочерними элементами.  
  
## <a name="use-hierarchies-and-collections-to-organize-members"></a>Использование иерархии и коллекций для организации элементов  
 Иерархии и коллекции можно использовать для группировки элементов для отчетов или анализа. Дополнительные сведения см. в разделах [Hierarchies &#40;Master Data Services&#41;](../master-data-services/hierarchies-master-data-services.md) и [Collections &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md).  
  
## <a name="member-example"></a>Пример элемента  
 В следующем примере каждый элемент состоит из значений атрибутов Name, Code, Subcategory, StandardCost, ListPrice и FilePhoto.  
  
 ![Таблица продукта «Велосипед»](../master-data-services/media/mds-conc-entity-table-w-data.gif "Таблица продукта «Велосипед»")  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание нового конечного элемента.|[Создание конечного элемента &#40;Master Data Services&#41;](../master-data-services/create-a-leaf-member-master-data-services.md)|  
|Создание нового объединенного элемента.|[Создание &#40;объединенного элемента Master Data Services&#41;](../master-data-services/create-a-consolidated-member-master-data-services.md)|  
|Удаление существующего элемента или коллекции.|[Удаление элемента или коллекции &#40;Master Data Services&#41;](../master-data-services/delete-a-member-or-collection-master-data-services.md)|  
|Повторная активация удаленного элемента или коллекции.|[Повторная активация элемента или коллекции &#40;Master Data Services&#41;](../master-data-services/reactivate-a-member-or-collection-master-data-services.md)|  
|Обновление значений атрибутов элемента.|[Измените тип атрибута &#40;надстройка MDS для Excel&#41;](../master-data-services/microsoft-excel-add-in/change-the-attribute-type-mds-add-in-for-excel.md)|  

  
## <a name="related-content"></a>См. также  
  
-   [Обзор Master Data Services &#40;MDS&#41;](../master-data-services/master-data-services-overview-mds.md)  
  
-   [Сущности &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
-   [Master Data Services &#40;атрибутов&#41;](../master-data-services/attributes-master-data-services.md)  
  
-   [Иерархии &#40;Master Data Services&#41;](../master-data-services/hierarchies-master-data-services.md)  
  
-   [&#40;коллекций Master Data Services&#41;](../master-data-services/collections-master-data-services.md)  
  
-   [Конечные разрешения &#40;Master Data Services&#41;](../master-data-services/leaf-permissions-master-data-services.md)  
  
 
-   [Операторы фильтров &#40;Master Data Services&#41;](../master-data-services/filter-operators-master-data-services.md)  
  
  
