---
title: Сущности (службы основных данных) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], about entities
- entities [Master Data Services]
ms.assetid: 0af057d5-6b73-472b-99eb-9f5eb61a9b5b
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 6f0888b95eb765313b2cf766b0f61c1d71f642b4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306044"
---
# <a name="entities-master-data-services"></a>Сущности (службы основных данных)
  Сущности — это объекты, которые содержатся в моделях [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Каждая сущность содержит элементы, которые являются строками основных данных, которыми можно управлять.  
  
## <a name="how-many-entities-are-appropriate"></a>Необходимо число сущностей  
 Модели могут содержать множество сущностей, которым нужно управлять. В каждой сущности должны объединяться схожие данные. Например, сущность может быть предназначена для всех корпоративных учетных записей или для главного списка сотрудников.  
  
 Как правило, существует одна или несколько центральных сущностей, важных для бизнеса, с которыми связаны другие объекты модели. Например, в модели «Продукт» можно иметь центральную сущность с названием «Продукт», с которой будут связаны другие сущности, такие как «Подкатегория» и «Категория». Однако нет необходимости в центральной сущности. В зависимости от потребностей можно иметь несколько сущностей, которые должны рассматриваться как равные по важности.  
  
## <a name="how-entities-relate-to-other-model-objects"></a>Связь сущностей с другими объектами модели  
 Сущность можно рассматривать как таблицу, содержащую основные данные, в которой строки представляют элементы, а столбцы — атрибуты.  
  
 ![Сущность служб Master Data Services, представленная в виде таблицы](../../2014/master-data-services/media/mds-conc-entity-table.gif "Сущность служб Master Data Services, представленная в виде таблицы")  
  
 Сущность заполняется перечнем основных данных, которыми нужно управлять.  
  
 Сущности могут использоваться для построения производных иерархий, которые являются многоуровневыми и основанными на нескольких сущностях. Дополнительные сведения см. в разделе [Производные иерархии (службы Master Data Services)](derived-hierarchies-master-data-services.md).  
  
 Сущности также могут содержать явные иерархии (неоднородные структуры на основе одной сущности) и коллекции (одноразовые комбинации подмножеств элементов). Дополнительные сведения см. в разделах [Явные иерархии (службы Master Data Services)](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) и [Коллекции (службы Master Data Services)](../../2014/master-data-services/collections-master-data-services.md).  
  
## <a name="using-entities-as-constrained-lists"></a>Использование сущностей в качестве ограниченных списков  
 Когда пользователи назначают атрибуты элементам в сущности, можно предоставить им выбор из ограниченного списка значений. Для этого используйте сущность для заполнения списка значений атрибута. Такой атрибут называется атрибутом на основе домена. Дополнительные сведения см. в разделе [Атрибуты на основе домена (службы Master Data Services)](../../2014/master-data-services/domain-based-attributes-master-data-services.md).  
  
## <a name="base-entities"></a>Базовые сущности  
 Базовая сущность является отправной точкой для пользователей при навигации по объектам в модели. Базовая сущность определяет макет экрана, когда пользователь открывает функциональную область **Обозреватель** и щелкает пункт **Обозреватель** на панели меню. Чтобы указать сущность в качестве базовой, необходимо перейти к функциональной области **Администрирование системы** . На странице **Представление модели** перетащите сущность из дерева с правой стороны на имя модели в дереве с левой стороны.  
  
## <a name="entity-security"></a>Безопасность сущности  
 Можно дать пользователям разрешения на сущность, которая включает связанные объекты модели. Дополнительные сведения см. в разделе [Разрешения сущности (службы Master Data Services)](../../2014/master-data-services/entity-permissions-master-data-services.md).  
  
## <a name="entity-examples"></a>Примеры сущности  
 В следующих примерах сущность имеет атрибуты: Name, Code, Subcategory, StandardCost, ListPrice и FilePhoto. Эти атрибуты описывают элементы. Каждый элемент представлен отдельной строкой значений атрибута.  
  
 ![Таблица продукта "Велосипед"](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Таблица продукта \"Велосипед\"")  
  
 В следующем примере сущность «Продукт» является центральной. Сущность «Подкатегория» является атрибутом на основе домена сущности «Продукт». Сущность «Категория» является атрибутом на основе домена сущности «Подкатегория». StandardCost и ListPrice — это атрибуты в свободной форме сущности Product, а FilePhoto — это файловый атрибут сущности Product.  
  
 ![Древовидная структура сущности "Продукт"](../../2014/master-data-services/media/mds-conc-entity-ui.gif "Древовидная структура сущности \"Продукт\"")  
  
> [!NOTE]  
>  Это пример на основе пользовательского интерфейса [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Иерархическая древовидная структура показывает отношения между сущностями и атрибутами на основе домена. Она предназначена для отображения отношений, а не для демонстрации уровней важности.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание новой сущности.|[Создать сущность &#40;службы Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md)|  
|Указание того, что сущность может содержать явные иерархии и коллекции.|[Активация сущности для явных иерархий и коллекций &#40;службы Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|  
|Изменение имени существующей сущности.|[Изменение имени сущности &#40;службы Master Data Services&#41;](edit-an-entity-master-data-services.md)|  
|Удаление существующей сущности.|[Удаление сущности &#40;службы Master Data Services&#41;](../../2014/master-data-services/delete-an-entity-master-data-services.md)|  
|Назначение разрешения сущностям.|[Назначение разрешений объекта модели &#40;службы Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Модели (службы Master Data Services)](../../2014/master-data-services/models-master-data-services.md)  
  
-   [Члены &#40;службы Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)  
  
-   [Атрибуты &#40;службы Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
