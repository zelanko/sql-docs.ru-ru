---
title: "Добавление атрибутов к измерениям | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 80551dad-97ac-40d0-90af-b810780321ce
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: d4d2a87b4e387d48c6f9537ee402a10a253bf202
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="lesson-2-3---adding-attributes-to-dimensions"></a>Занятие 2-3-Добавление атрибутов к измерениям
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]Теперь, после определения измерений, их можно заполнить с атрибутами, которые представляют все элементы данных в измерении. Атрибуты обычно основаны на полях из представления источников данных. При добавлении атрибутов в измерение можно включить поля из любой таблицы в представлении источника данных.  
  
В этой задаче с помощью конструктора измерений в измерения «Заказчик» и «Продукт» будут добавлены атрибуты. Измерение «Заказчик» будет включать атрибуты, основанные на полях из таблиц как «Заказчик», так и «География».  
  
## <a name="adding-attributes-to-the-customer-dimension"></a>Добавление атрибутов в измерение «Заказчик»  
  
#### <a name="to-add-attributes"></a>Добавление атрибутов  
  
1.  Откройте в конструкторе измерений измерение «Заказчик». Для этого дважды щелкните измерение **Заказчик** в узле **Измерения** обозревателя решений.  
  
2.  На панели **Атрибуты** обратите внимание на атрибуты «Customer Key» и «Geography Key», созданные мастером кубов.  
  
3.  На панели инструментов вкладки **Структура измерения** щелкните значок «Масштаб», чтобы просмотреть таблицы области **Представление источника данных** в масштабе 100 %.  
  
4.  Перетащите следующие столбцы из таблицы **Customer** в области **Представление источника данных** в область **Атрибуты** .  
  
    -   **BirthDate**  
  
    -   **MaritalStatus**  
  
    -   **Gender**  
  
    -   **EmailAddress**  
  
    -   **YearlyIncome**  
  
    -   **TotalChildren**  
  
    -   **NumberChildrenAtHome**  
  
    -   **EnglishEducation**  
  
    -   **EnglishOccupation**  
  
    -   **HouseOwnerFlag**  
  
    -   **NumberCarsOwned**  
  
    -   **Phone**  
  
    -   **DateFirstPurchase**  
  
    -   **CommuteDistance**  
  
5.  Перетащите следующие столбцы из таблицы **Geography** в области **Представление источника данных** в область **Атрибуты** .  
  
    -   **Город**  
  
    -   **StateProvinceName**  
  
    -   **EnglishCountryRegionName**  
  
    -   **PostalCode**  
  
6.  В меню «Файл» выберите команду **Сохранить все**.  
  
## <a name="adding-attributes-to-the-product-dimension"></a>Добавление атрибутов в измерение «Продукт»  
  
#### <a name="to-add-attributes"></a>Добавление атрибутов  
  
1.  Откройте в конструкторе измерений измерение «Продукт». Дважды щелкните измерение **Продукт** в обозревателе решений.  
  
2.  На панели **Атрибуты** обратите внимание на атрибут «Ключ продукта», созданный мастером кубов.  
  
3.  На панели инструментов вкладки **Структура измерения** щелкните значок «Масштаб», чтобы просмотреть таблицы области **Представление источника данных** в масштабе 100 %.  
  
4.  Перетащите следующие столбцы из таблицы **Продукт** в области **Представление источника данных** в область **Атрибуты** .  
  
    -   **StandardCost**  
  
    -   **Color**  
  
    -   **SafetyStockLevel**  
  
    -   **ReorderPoint**  
  
    -   **ListPrice**  
  
    -   **Размер**  
  
    -   **SizeRange**  
  
    -   **Weight**  
  
    -   **DaysToManufacture**  
  
    -   **ProductLine**  
  
    -   **DealerPrice**  
  
    -   **Class**  
  
    -   **Style**  
  
    -   **ModelName**  
  
    -   **StartDate**  
  
    -   **EndDate**  
  
    -   **Состояние**  
  
5.  В меню «Файл» выберите команду **Сохранить все**.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Просмотр свойств куба и измерения](../analysis-services/lesson-2-4-reviewing-cube-and-dimension-properties.md)  
  
## <a name="see-also"></a>См. также:  
[Справочник по свойствам атрибута измерения](../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
  
