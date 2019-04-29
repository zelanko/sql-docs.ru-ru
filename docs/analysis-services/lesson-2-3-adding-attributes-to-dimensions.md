---
title: Добавление атрибутов к измерениям | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 753aad68d1c6fc9fb6fe53efb3b73ae767b4570e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63046016"
---
# <a name="lesson-2-3---adding-attributes-to-dimensions"></a>Урок 2 – 3-добавление к измерениям атрибутов
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

Теперь после определения измерений можно наполнить их атрибутами, которые представляют все элементы данных в измерении. Атрибуты обычно основаны на полях из представления источников данных. При добавлении атрибутов в измерение можно включить поля из любой таблицы в представлении источника данных.  
  
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
  
## <a name="see-also"></a>См. также  
[Справочник по свойствам атрибута измерения](../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
  
