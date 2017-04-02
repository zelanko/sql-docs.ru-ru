---
title: "Новые возможности служб SQL Server Analysis Services&#160;vNext | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1eb6afc9-76ed-45a2-a188-374a4fc23224
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 13
---
# Новые возможности служб SQL Server Analysis Services&#160;vNext
[!INCLUDE[tsql-appliesto-ssvNxt-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

## <a name="sql-server-analysis-services-on-windows-ctp-12"></a>Службы SQL Server Analysis Services в Windows CTP 1.2

В этом выпуске нет новых функций. В число улучшений входят исправления ошибок и повышение производительности.

Последняя предварительная версия SQL Server Data Tools (SSDT), аналогичная версии SQL Server vNext CTP 1.2, дополнена новыми современными возможностями получения данных, которые были представлены в версии CTP 1.1 вместе с новым меню редактора запросов и функцией быстрого доступа. 

## <a name="sql-server-analysis-services-on-windows-ctp-11"></a>Службы SQL Server Analysis Services в Windows CTP 1.1 

В этом выпуске представлены улучшения для табличных моделей. 

### <a name="1400-compatibility-level-for-tabular-models"></a>Уровень совместимости 1400 для табличных моделей
  Для использования возможностей и функций, описываемых в этом разделе, для новых или существующих табличных моделей необходимо задать уровень совместимости 1400. Модели с уровнем совместимости 1400 нельзя развертывать в SQL Server 2016 с пакетом обновления 1 (SP1) или более ранней версии либо переводить на более низкий уровень совместимости.
  
  Чтобы создать новый проект табличной модели с уровнем совместимости 1400 или перевести существующий проект на этот уровень, скачайте и установите **предварительный выпуск** [SQL Server Data Tools (SSDT) 17.0 RC2](https://go.microsoft.com/fwlink?LinkId=837939). 
  
В SSDT можно выбрать новый уровень совместимости 1400 при создании проектов табличной модели. 

![AS_NewTabular1400Project](../analysis-services/media/as-newtabular1400project.png)

>[!NOTE] Интегрированная рабочая область в декабрьском выпуске SQL Server Data Tools (SSDT) поддерживает уровень совместимости 1400. При создании проектов табличной модели в экземпляре сервера рабочей области этот экземпляр или любой экземпляр, в котором производится развертывание, должен иметь версию [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 1.1. 

Чтобы обновить существующую табличную модель в SSDT, в обозревателе решений щелкните правой кнопкой мыши **Model.bim**, а затем в окне **Свойства** присвойте свойству **Уровень совместимости** значение **SQL Server vNext (1400)**. 

![AS_Model_Properties](../analysis-services/media/as-model-properties.png)

### <a name="modern-get-data-experience"></a>Современный интерфейс получения данных
В последнем предварительном выпуске SQL Server Data Tools (SSDT), который соответствует выпуску [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 1.1, появился современный интерфейс **получения данных** для табличных моделей с уровнем совместимости 1400. Он основан на аналогичном интерфейсе в Power BI Desktop и Microsoft Excel 2016.

![AS_Get_Data_in_SSDT](../analysis-services/media/as-get-data-in-ssdt.png)

>[!NOTE] В этом выпуске поддерживается ограниченный набор источников данных. В будущих обновлениях будут поддерживаться дополнительные источники данных и возможности.

Дополнительные сведения о современном интерфейсе получения данных см. в [блоге команды разработчиков служб Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2016/12/16/introducing-a-modern-get-data-experience-for-sql-server-vnext-on-windows-ctp-1-1-for-analysis-services/).

## <a name="ragged-hierarchies"></a>Неоднородные иерархии
В табличных моделях можно моделировать иерархии типа "родители-потомки". Иерархии с разным количеством уровней часто называют неоднородными. По умолчанию неоднородные иерархии отображаются с пустыми полями для уровней ниже последнего дочернего уровня. Вот пример неоднородной иерархии на организационной диаграмме:

![AS_Ragged_Hierarchy](../analysis-services/media/as-ragged-hierarchy.png)

В этом выпуске появилось свойство **Скрыть члены**. Свойству **Скрыть члены** иерархии можно присвоить значение **Скрыть пустые члены**.

![AS_Hide_Blank_Members](../analysis-services/media/as-hide-blank-members.png)

 >[!NOTE] Пустые члены в модели представлены пустым значением DAX, а не пустой строкой.

Если задано значение **Скрыть пустые члены** и модель развернута, более удобную для восприятия версию иерархии можно просмотреть в таких клиентских средствах создания отчетов, как Excel.

![AS_Non_Ragged_Hierarchy](../analysis-services/media/as-non-ragged-hierarchy.png)

### <a name="detail-rows"></a>Строки детализации
Теперь можно определить настраиваемый набор строк, на основе которого формируется значение меры. Строки детализации похожи на действие детализации по умолчанию в многомерных моделях. Это позволяет конечным пользователям просматривать более подробные данные, чем на агрегированном уровне. 

На приведенной ниже сводной таблице представлен объем продаж в Интернете по годам из образца табличной модели Adventure Works. Вы можете щелкнуть правой кнопкой мыши ячейку с агрегированным значением меры, а затем выбрать пункт **Показать подробности**, чтобы просмотреть строки детализации.

![AS_Show_Details](../analysis-services/media/as-show-details.png)

По умолчанию отображаются связанные данные из таблицы продаж в Интернете. Такие ограниченные возможности зачастую бесполезны для пользователя, так как таблица может не содержать столбцы, включающие нужную информацию, например имя клиента и сведения о заказе. С помощью строк детализации можно указать свойство **Выражение свойств детализации** для мер.

#### <a name="detail-rows-expression-property-for-measures"></a>Свойство "Выражение строк детализации" для мер
Свойство **Выражение свойств детализации** для мер позволяет создателям моделей настраивать столбцы и строки, возвращаемые конечным пользователям.

![AS_Detail_Rows_Expression_Property](../analysis-services/media/as-detail-rows-expression-property.png)

Функция DAX [SELECTCOLUMNS](https://msdn.microsoft.com/library/mt761759.aspx) часто используется в выражении строк детализации. В приведенном ниже примере определяются столбцы, возвращаемые для строк в таблице продаж в Интернете в образце табличной модели Adventure Works.

```
SELECTCOLUMNS(
    'Internet Sales',
    "Customer First Name", RELATED( Customer[Last Name]),
    "Customer Last Name", RELATED( Customer[First Name]),
    "Order Date", 'Internet Sales'[Order Date],
    "Internet Total Sales", [Internet Total Sales]
)
```

Когда свойство определено и модель развернута, настраиваемый набор строк возвращается при выборе пользователем команды **Показать подробности**. Контекст фильтра выбранной ячейки учитывается автоматически. В этом примере отображаются только строки для значения 2010.

![AS_Detail_Rows](../analysis-services/media/as-detail-rows.png)

#### <a name="default-detail-rows-expression-property-for-tables"></a>Свойство "Выражение строк детализации по умолчанию" для таблиц
Так же как и меры, таблицы имеют свойство для определения выражения строк детализации. Свойство **Выражение строк детализации по умолчанию** используется по умолчанию для всех мер в таблице. Меры, для которых не определено собственное выражение, наследуют выражение от таблицы и отображают набор строк, определенный для таблицы. Это позволяет повторно использовать выражения, а новые меры, добавляемые в таблицу позднее, автоматически наследуют выражение.

![AS_Default_Detail_Rows_Expression](../analysis-services/media/as-default-detail-rows-expression.png)
 
#### <a name="detailrows-dax-function"></a>Функция DAX DETAILROWS
В этом выпуске появилась функция DAX `DETAILROWS`, которая возвращает набор строк, определяемый выражением строк детализации. Она действует аналогично инструкции `DRILLTHROUGH` в MDX, которая также совместима с выражениями строк детализации, определенными в табличных моделях.

Приведенный ниже запрос DAX возвращает набор строк, определенный выражением строк детализации для меры или ее таблицы. Если выражение не определено, возвращаются данные таблицы продаж в Интернете, так как она содержит меру.

```
EVALUATE DETAILROWS([Internet Total Sales])
```

## <a name="dax-enhancements"></a>Улучшения DAX
В этот выпуск входит оператор `IN` для выражений DAX. Она аналогична оператору [`TSQL IN`](https://msdn.microsoft.com/library/ms177682.aspx), обычно используемому для указания нескольких значений в предложении `WHERE`.

Ранее многозначные фильтры обычно задавались с помощью логического оператора `OR`, как в следующем выражении меры:

```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
                 'Product'[Color] = "Red"
            || 'Product'[Color] = "Blue"
            || 'Product'[Color] = "Black"
    )
```

С помощью оператора `IN` это стало проще:
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales], 'Product'[Color] IN { "Red", "Blue", "Black" }
    )
```

В этом случае оператор `IN` ссылается на таблицу с одним столбцом и тремя строками — по одному из каждых указанных цветов. Обратите внимание на то, что синтаксис конструктора таблицы предусматривает использование фигурных скобок.

Оператор `IN` функционально эквивалентен функции `CONTAINSROW`.
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales], CONTAINSROW({ "Red", "Blue", "Black" }, 'Product'[Color])
    )
```

Оператор `IN` также можно эффективно использовать с конструкторами таблиц. Например, следующая мера выполняет фильтрацию по сочетанию цвета и категории продукта:
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
        FILTER( ALL('Product'),
              ( 'Product'[Color] = "Red"   && Product[Product Category Name] = "Accessories" )
         || ( 'Product'[Color] = "Blue"  && Product[Product Category Name] = "Bikes" )
         || ( 'Product'[Color] = "Black" && Product[Product Category Name] = "Clothing" )
        )
    )
```

Благодаря новому оператору `IN` приведенное выше выражение меры эквивалентно следующему:
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
        FILTER( ALL('Product'),
            ('Product'[Color], Product[Product Category Name]) IN
            { ( "Red", "Accessories" ), ( "Blue", "Bikes" ), ( "Black", "Clothing" ) }
        )
    )
```


## <a name="table-level-security"></a>Безопасность на уровне таблицы
В этом выпуске реализована безопасность на уровне таблицы. Помимо ограничения доступа к данным таблиц, можно защищать имена конфиденциальных таблиц. Благодаря этому злоумышленник не сможет узнать о существовании этих таблиц.

Безопасность на уровне таблиц настраивается с помощью метаданных на основе JSON, языка TMSL или табличной модели объектов (TOM). 

Например, приведенный ниже код позволяет защитить таблицу Product в образце табличной модели Adventure Works путем присвоения свойству **MetadataPermission** класса **TablePermission** значения **None**.

```
//Find the Users role in Adventure Works and secure the Product table
ModelRole role = db.Model.Roles.Find("Users");
Table productTable = db.Model.Tables.Find("Product");
if (role != null && productTable != null)
{
    TablePermission tablePermission;
    if (role.TablePermissions.Contains(productTable.Name))
    {
        tablePermission = role.TablePermissions[productTable.Name];
    }
    else
    {
        tablePermission = new TablePermission();
        role.TablePermissions.Add(tablePermission);
        tablePermission.Table = productTable;
    }
    tablePermission.MetadataPermission = MetadataPermission.None;
}
db.Update(UpdateOptions.ExpandFull);
```
## <a name="future-updates"></a>Будущие обновления
В будущем выпуске появятся дополнительные улучшения. В этой статье будут публиковаться объявления о новых важных возможностях SQL Server vNext.
