---
title: 'Занятие 3: Переименование столбцов | Документы Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5fc8ba1a-2b30-4775-9b3b-c09dee711b3e
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ed2f495f4300abca78b3a1b7597bd0d09fd15292
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095584"
---
# <a name="lesson-3-rename-columns"></a>Занятие 3. Переименование столбцов
  На этом занятии мы переименуем несколько столбцов в каждой импортированной таблице. Переименование делает названия столбцов более понятными, и с ними становится легче работать в конструкторе моделей, а также при выборе полей в клиентском приложении. Дополнительные сведения см. в разделе [Переименование таблицы или столбца (табличные службы SSAS)](tabular-models/rename-a-table-or-column-ssas-tabular.md).  
  
> [!IMPORTANT]  
>  Переименование столбцов не требуется для завершения этого учебника. Однако в оставшихся занятиях, в частности занятиях, включающих создание связей, а также вычисляемых столбцов и мер с помощью DAX-формул, будут упоминаться понятные имена столбцов, которые будут назначены в ходе этого занятия. Если не переименовывать столбцы, нужно будет изменить DAX-формулы в занятиях 5, 6 и 7 для использования имен исходных столбцов, указанных в этом занятии.  
  
 Предполагаемое время выполнения данного занятия: **20 минут**  
  
## <a name="prerequisites"></a>предварительные требования  
 Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Прежде чем выполнять задания в этом занятии, необходимо завершить предыдущее занятие: [Занятие 2. Добавление данных](lesson-2-add-data.md).  
  
## <a name="rename-columns"></a>Переименование столбцов  
  
#### <a name="to-rename-columns"></a>Переименование столбцов  
  
1.  В конструкторе моделей щелкните таблицу (вкладку) **Заказчик** .  
  
     При выборе вкладки соответствующая таблица становится активной в окне конструктора моделей.  
  
2.  Дважды щелкните **CustomerKey** столбца и введите `Customer  Id`, а затем нажмите клавишу ВВОД.  
  
    > [!TIP]  
    >  Столбец также можно переименовать в свойстве **Имя столбца** в окне **Свойства** столбца или в представлении диаграммы.  
  
3.  Переименуйте оставшиеся столбцы в таблице **Заказчик** , а также столбцы в оставшихся таблицах, заменив исходное имя понятным именем.  
  
     **Таблица Customer**  
  
    |Имя источника|Понятное имя|  
    |-----------------|-------------------|  
    |GeographyKey|Geography Id|  
    |CustomerAlternateKey|Customer Alternate Id|  
    |FirstName|First Name|  
    |MiddleName|Второе имя|  
    |LastName|Last Name|  
    |NameStyle|Стиль имени|  
    |BirthDate|Birth Date|  
    |MaritalStatus|Семейное положение|  
    |EmailAddress|Email Address|  
    |YearlyIncome|Годовой доход|  
    |TotalChildren|Общее количество детей|  
    |NumberChildrenAtHome|Количество детей в доме|  
    |EnglishEducation|Образование|  
    |EnglishOccupation|Род занятий|  
    |HouseOwnerFlag|Владеет домом|  
    |NumberCarsOwned|Количество машин во владении|  
    |AddressLine1|Строка адреса 1|  
    |AddressLine2|Строка адреса 2|  
    |Phone|Номер телефона|  
    |DateFirstPurchase|Дата первой покупки|  
    |CommuteDistance|Расстояние до работы|  
  
     **Дата**  
  
    |Имя источника|Понятное имя|  
    |-----------------|-------------------|  
    |FullDateAlternateKey|Дата|  
    |DayNumberOfWeek|Номер дня недели|  
    |EnglishDayNameOfWeek|День недели|  
    |DayNumberOfMonth|День месяца|  
    |DayNumberOfYear|День года|  
    |WeekNumberOfYear|Номер недели года|  
    |EnglishMonthName|Названия месяца|  
    |MonthNumberOfYear|Месяц|  
    |CalendarQuarter|Calendar Quarter|  
    |CalendarYear|Calendar Year|  
    |CalendarSemester|Calendar Semester|  
    |FiscalQuarter|Финансовый квартал|  
    |FiscalYear|Финансовый год|  
    |FiscalSemester|Финансовый семестр|  
  
     **Geography**  
  
    |Имя источника|Понятное имя|  
    |-----------------|-------------------|  
    |GeographyKey|Geography Id|  
    |StateProvinceCode|Код штата или провинции|  
    |StateProvinceName|Название штата или провинции|  
    |CountryRegionCode|Код региона или страны|  
    |EnglishCountryRegionName|Название региона или страны|  
    |PostalCode|Почтовый индекс|  
    |SalesTerritoryKey|Идентификатор территории продаж|  
  
     **Продукт**  
  
    |Имя источника|Понятное имя|  
    |-----------------|-------------------|  
    |ProductKey|Product Id|  
    |ProductAlternateKey|Product Alternate Id|  
    |ProductSubcategoryKey|Идентификатор подкатегории продукта|  
    |WeightUnitMeasureCode|Код веса единицы|  
    |SizeUnitMeasureCode|Код размера единицы|  
    |EnglishProductName|Название продукта|  
    |StandardCost|Standard Cost|  
    |FinishedGoodsFlag|Является готовым продуктом|  
    |SafetyStockLevel|Safety Stock Level|  
    |ReorderPoint|Reorder Point|  
    |ListPrice|List Price|  
    |SizeRange|Size Range|  
    |DaysToManufacture|Дни производства|  
    |ProductLine|Линейка продуктов|  
    |Dealer Price|Dealer Price|  
    |ModelName|Имя модели|  
    |LargePhoto|Большое изображение|  
    |EnglishDescription|Описание|  
    |StartDate|Дата начала жизненного цикла продукта (Дата начала периода расчета стоимости продукта )|  
    |EndDate|Дата окончания жизненного цикла продукта (Дата окончания периода расчета стоимости продукта)|  
    |Состояние|Состояние продукта|  
  
     **Категория продукта**  
  
    |Имя источника|Понятное имя|  
    |-----------------|-------------------|  
    |ProductCategoryKey|Идентификатор категории продукта|  
    |ProductCategoryAlternateKey|Альтернативный идентификатор категории продукта|  
    |EnglishProductCategoryName|Имя категории продукта|  
  
     **Подкатегория продукта**  
  
    |Имя источника|Понятное имя|  
    |-----------------|-------------------|  
    |ProductSubcategoryKey|Идентификатор подкатегории продукта|  
    |ProductSubcategoryAlternateKey|Альтернативный идентификатора подкатегории продукта|  
    |EnglishProductSubcategoryName|Имя подкатегории продукта|  
    |ProductCategoryKey|Идентификатор категории продукта|  
  
     **Internet Sales**  
  
    |Имя источника|Понятное имя|  
    |-----------------|-------------------|  
    |ProductKey|Product Id|  
    |CustomerKey|Customer Id|  
    |PromotionKey|Идентификатор продвижения|  
    |CurrencyKey|Идентификатор валюты|  
    |SalesTerritoryKey|Идентификатор территории продаж|  
    |SalesOrderNumber|Число заказов на продажу|  
    |SalesOrderLineNumber|Число линий заказов на продажу|  
    |RevisionNumber|Revision Number|  
    |OrderQuantity|Заказанное количество|  
    |UnitPrice|Unit Price|  
    |ExtendedAmount|Extended Amount|  
    |UnitPriceDiscountPct|Процент скидки от стоимости единицы|  
    |DiscountAmount|Discount Amount|  
    |ProductStandardCost|Product Standard Cost|  
    |TotalProductCost|Total Product Cost|  
    |SalesAmount|Объем продаж|  
    |TaxAmt|Tax Amt|  
    |CarrierTrackingNumber|Номер отслеживания перевозчика|  
    |CustomerPONumber|Номер почтового отделения клиента|  
    |OrderDate|Дата заказа|  
    |DueDate|Дата оплаты счета|  
    |ShipDate|Дата отгрузки|  
  
## <a name="next-step"></a>Следующий шаг  
 Чтобы продолжить изучение этого учебника, перейдите к следующему занятию: [Занятие 4. Диалоговое окно "Пометить как таблицу дат"](lesson-3-mark-as-date-table.md).  
  
  