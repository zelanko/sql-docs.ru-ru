---
title: Сущности
description: Сущности — это объекты, содержащиеся в Master Data Services моделях. Каждая сущность содержит элементы, которые являются строками основных данных, которыми можно управлять.
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], about entities
- entities [Master Data Services]
ms.assetid: 0af057d5-6b73-472b-99eb-9f5eb61a9b5b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5c40c4cd565d01e7918cecd7c2dc89015f13c9f9
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85811977"
---
# <a name="entities-master-data-services"></a>Сущности (службы основных данных)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Сущности — это объекты, которые содержатся в моделях [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Каждая сущность содержит элементы, которые являются строками основных данных, которыми можно управлять.  
  
## <a name="how-many-entities-are-appropriate"></a>Необходимо число сущностей  
 Модели могут содержать множество сущностей, которым нужно управлять. В каждой сущности должны объединяться схожие данные. Например, сущность может быть предназначена для всех корпоративных учетных записей или для главного списка сотрудников.  
  
 Как правило, существует одна или несколько центральных сущностей, важных для бизнеса, с которыми связаны другие объекты модели. Например, в модели «Продукт» можно иметь центральную сущность с названием «Продукт», с которой будут связаны другие сущности, такие как «Подкатегория» и «Категория». Однако нет необходимости в центральной сущности. В зависимости от потребностей можно иметь несколько сущностей, которые должны рассматриваться как равные по важности.  
  
## <a name="how-entities-relate-to-other-model-objects"></a>Связь сущностей с другими объектами модели  
 Сущность можно рассматривать как таблицу, содержащую основные данные, в которой строки представляют элементы, а столбцы — атрибуты.  
  
 ![Сущность служб Master Data Services, представленная в виде таблицы](../master-data-services/media/mds-conc-entity-table.gif "Сущность служб Master Data Services, представленная в виде таблицы")  
  
 Сущность заполняется перечнем основных данных, которыми нужно управлять.  
  
 Сущности могут использоваться для построения производных иерархий, которые являются многоуровневыми и основанными на нескольких сущностях. Дополнительные сведения см. в разделе [Производные иерархии (службы Master Data Services)](../master-data-services/derived-hierarchies-master-data-services.md).  
  
 Сущности также могут содержать явные иерархии (неоднородные структуры на основе одной сущности) и коллекции (одноразовые комбинации подмножеств элементов). Дополнительные сведения см. в разделах [Явные иерархии (службы Master Data Services)](../master-data-services/explicit-hierarchies-master-data-services.md) и [Коллекции (службы Master Data Services)](../master-data-services/collections-master-data-services.md).  
  
## <a name="using-entities-as-constrained-lists"></a>Использование сущностей в качестве ограниченных списков  
 Когда пользователи назначают атрибуты элементам в сущности, можно предоставить им выбор из ограниченного списка значений. Для этого используйте сущность для заполнения списка значений атрибута. Такой атрибут называется атрибутом на основе домена. Дополнительные сведения см. в разделе [Атрибуты на основе домена (службы Master Data Services)](../master-data-services/domain-based-attributes-master-data-services.md).  
  
## <a name="base-entities"></a>Базовые сущности  
 Базовая сущность является отправной точкой для пользователей при навигации по объектам в модели. Базовая сущность определяет макет экрана, когда пользователь открывает функциональную область **Обозреватель** и щелкает пункт **Обозреватель** на панели меню. Чтобы указать сущность в качестве базовой, необходимо перейти к функциональной области **Администрирование системы** . На странице **Представление модели** перетащите сущность из дерева с правой стороны на имя модели в дереве с левой стороны.  
  
## <a name="entity-security"></a>Безопасность сущности  
 Можно дать пользователям разрешения на сущность, которая включает связанные объекты модели. Дополнительные сведения см. в разделе [Разрешения сущности (службы Master Data Services)](../master-data-services/entity-permissions-master-data-services.md).  
  
## <a name="entity-examples"></a>Примеры сущности  
 В следующих примерах сущность имеет атрибуты: Name, Code, Subcategory, StandardCost, ListPrice и FilePhoto. Эти атрибуты описывают элементы. Каждый элемент представлен отдельной строкой значений атрибута.  
  
 ![Таблица продукта «Велосипед»](../master-data-services/media/mds-conc-entity-table-w-data.gif "Таблица продукта «Велосипед»")  
  
 В следующем примере сущность «Продукт» является центральной. Сущность «Подкатегория» является атрибутом на основе домена сущности «Продукт». Сущность «Категория» является атрибутом на основе домена сущности «Подкатегория». StandardCost и ListPrice — это атрибуты в свободной форме сущности Product, а FilePhoto — это файловый атрибут сущности Product.  
  
 ![Древовидная структура сущности «Продукт»](../master-data-services/media/mds-conc-entity-ui.gif "Древовидная структура сущности «Продукт»")  
  
> [!NOTE]  
>  Это пример на основе пользовательского интерфейса [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Иерархическая древовидная структура показывает отношения между сущностями и атрибутами на основе домена. Она предназначена для отображения отношений, а не для демонстрации уровней важности.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание новой сущности.|[Создание сущности (службы Master Data Services)](../master-data-services/create-an-entity-master-data-services.md)|  
|Изменение имени существующей сущности.|[Изменение сущности (службы Master Data Services)](../master-data-services/edit-an-entity-master-data-services.md)|  
|Удаление существующей сущности.|[Удаление сущности (службы Master Data Services)](../master-data-services/delete-an-entity-master-data-services.md)|  
|Назначение разрешения сущностям.|[Назначение разрешения для объекта модели (службы Master Data Services)](../master-data-services/assign-model-object-permissions-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Модели (службы Master Data Services)](../master-data-services/models-master-data-services.md)  
  
-   [Элементы (службы Master Data Services)](../master-data-services/members-master-data-services.md)  
  
-   [Атрибуты (службы Master Data Services)](../master-data-services/attributes-master-data-services.md)  
  
  
