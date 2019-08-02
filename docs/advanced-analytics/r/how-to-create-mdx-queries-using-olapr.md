---
title: Создание запросов многомерных выражений в R с помощью средства OLAP
description: Используйте библиотеку пакетов OLAP в SQL Server для написания запросов многомерных выражений в скрипте языка R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/22/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: db9afc06a02825b8db449492d8cec6ee6d67801d
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715125"
---
# <a name="how-to-create-mdx-queries-in-r-using-olapr"></a>Создание запросов многомерных выражений в R с помощью средства OLAP
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Пакет [OLAP](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) поддерживает запросы многомерных выражений к кубам, размещенным в SQL Server Analysis Services. Можно создать запрос к существующему Кубу, просмотреть измерения и другие объекты куба, а также вставить существующие запросы многомерных выражений для получения данных.

В этой статье описываются два основных использования пакета **OLAP** .

+ [Создание запроса многомерных выражений из R с помощью конструкторов, предоставленных в пакете OLAP](#buildMDX)
+ [Выполнение существующего, допустимого запроса многомерных выражений с помощью средства OLAP и поставщика OLAP](#executeMDX)

Следующие операции не поддерживаются:

+ Запросы DAX к табличной модели
+ Создание новых объектов OLAP
+ Обратная запись в секции, включая меры или суммы

## <a name="buildMDX"></a>Построение запроса многомерных выражений из R

1. Определите строку подключения, указывающую источник данных OLAP (экземпляр служб SQL Server Analysis Services ) и поставщик MSOLAP.

2. Используйте функцию `OlapConnection(connectionString)` , чтобы создать дескриптор для запроса многомерных выражений и передать строку подключения.

3. Используйте конструктор `Query()` для создания экземпляра объекта запроса.

4. Используйте следующие вспомогательные функции, чтобы предоставить дополнительные сведения об измерениях и мерах для включения в запрос многомерных выражений:

     + `cube()` Укажите имя базы данных SSAS. При подключении к именованному экземпляру укажите имя компьютера и имя экземпляра. 
     + `columns()`Укажите имена мер для использования в аргументе **On Columns** .
     + `rows()`Укажите имена мер для использования в аргументе **On Rows** .
     + `slicers()` Укажите поле или элементы для использования в качестве среза. Срез аналогичен фильтру, который применяется ко всем данным запроса многомерных выражений.
     
     + `axis()` Укажите имя дополнительной оси для использования в запросе. 
     
         Куб OLAP может содержать до 128 осей запроса. Как правило, первые четыре оси называются столбцами, **строками**, **страницами**и **главами**. 
         
         Если запрос относительно прост, для его создания можно использовать функции `columns`, `rows`и т. п. Однако можно также использовать функцию `axis()` с ненулевым значением индекса для создания запроса многомерных выражений с несколькими квалификаторами или для добавления дополнительных измерений в качестве квалификаторов.

5. Передайте этот обработчик и завершенный запрос многомерных выражений в одну из следующих функций, в зависимости от формы результатов. 

  + `executeMD` возвращает многомерный массив.
  + `execute2D` возвращает двухмерный (табличный) кадр данных.

## <a name="executeMDX"></a>Выполнение допустимого запроса многомерных выражений из R

1. Определите строку подключения, указывающую источник данных OLAP (экземпляр служб SQL Server Analysis Services ) и поставщик MSOLAP.

2. Используйте функцию `OlapConnection(connectionString)` , чтобы создать дескриптор для запроса многомерных выражений и передать строку подключения.

3. Определите переменную R для хранения текста запроса многомерных выражений.

4. Передайте дескриптор и переменную, содержащую запрос многомерных выражений, в функции `executeMD` или `execute2D`в зависимости от вида результатов.

    + `executeMD` возвращает многомерный массив.
    + `execute2D` возвращает двухмерный (табличный) кадр данных.

## <a name="examples"></a>Примеры

Следующие примеры основаны на киоске данных AdventureWorks и проекте Куба, так как этот проект широко доступен в нескольких версиях, включая файлы резервных копий, которые можно легко восстановить в Analysis Services. Если у вас нет Куба, получите пример куба, используя один из следующих вариантов:

+ Создайте куб, используемый в этих примерах, следуя Analysis Services учебнике до занятия 4. [Создание куба OLAP](../../analysis-services/multidimensional-tutorial/multidimensional-modeling-adventure-works-tutorial.md)

+ Скачайте существующий куб в качестве резервной копии и восстановите его в экземпляре Analysis Services. Например, этот сайт предоставляет полностью обработанный куб в формате ZIP: [Многомерная модель Adventure Works SQL 2014](https://msftdbprodsamples.codeplex.com/downloads/get/882334). Извлеките файл и восстановите его в экземпляре SSAS. Дополнительные сведения см. в статье командлет [Backup and Restore](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)или RESTORE [-ASDatabase](../../analysis-services/powershell/restore-asdatabase-cmdlet.md).

### <a name="1-basic-mdx-with-slicer"></a>1. Базовое многомерное выражение со срезом

Этот запрос многомерных выражений выбирает _меры_ для количества и объема продаж через Интернет и размещает их на оси столбцов. Она добавляет элементы измерения SalesTerritory в качестве *среза*для фильтрации запроса, чтобы в вычислениях использовались только данные по продажам из Австралии.

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, 
{[Product].[Product Line].[Product Line].MEMBERS} ON ROWS 
FROM [Analysis Services Tutorial] 
WHERE [Sales Territory].[Sales Territory Country].[Australia]
```

+ В столбцах можно указать несколько мер в виде элементов строки с разделителями-запятыми.
+ Ось строк использует все возможные значения (все элементы) измерения Product Line. 
+ Этот запрос возвращает таблицу с тремя столбцами, _содержащей сводку по_ продажам через Интернет из всех стран.
+ Предложение WHERE задает _ось среза_. В этом примере срез использует элемент измерения **SalesTerritory** для фильтрации запроса таким образом, чтобы в вычислениях использовались только продажи из Австралии.

#### <a name="to-build-this-query-using-the-functions-provided-in-olapr"></a>Создание этого запроса с помощью функций, предоставленных в olapR

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs <- OlapConnection(cnnstr)

qry <- Query()
cube(qry) <- "[Analysis Services Tutorial]"
columns(qry) <- c("[Measures].[Internet Sales Count]", "[Measures].[Internet Sales-Sales Amount]")
rows(qry) <- c("[Product].[Product Line].[Product Line].MEMBERS") 
slicers(qry) <- c("[Sales Territory].[Sales Territory Country].[Australia]")

result1 <- executeMD(ocs, qry)

```

Для именованного экземпляра не забудьте экранировать все символы, которые могут считаться управляющими символами в R.  Например, следующая строка подключения ссылается на экземпляр OLAP01 на сервере с именем Контосохк:

```R
cnnstr <- "Data Source=ContosoHQ\\OLAP01; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
```

#### <a name="to-run-this-query-as-a-predefined-mdx-string"></a>Выполнение этого запроса в качестве заранее определенной строки многомерного выражения

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs <- OlapConnection(cnnstr)

mdx <- "SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, {[Product].[Product Line].[Product Line].MEMBERS} ON ROWS FROM [Analysis Services Tutorial] WHERE [Sales Territory].[Sales Territory Country].[Australia]"

result2 <- execute2D(ocs, mdx)
```

Если вы определяете запрос с помощью конструктора многомерных выражений в SQL Server Management Studio а затем сохраняете строку многомерного выражения, она будет нумеровать оси, начиная с 0, как показано ниже: 

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[Internet Sales-Sales Amount]} ON AXIS(0), 
   {[Product].[Product Line].[Product Line].MEMBERS} ON AXIS(1) 
   FROM [Analysis Services Tutorial] 
   WHERE [Sales Territory].[Sales Territory Countr,y].[Australia]
```

При этом данный запрос все равно можно выполнить в качестве заранее определенной строки многомерного выражения. Однако, чтобы создать тот же запрос с помощью `axis()` функции R, используя функцию, необходимо перенумеровать оси, начиная с 1.

### <a name="2-explore-cubes-and-their-fields-on-an-ssas-instance"></a>2. Просмотр кубов и их полей в экземпляре SSAS

Вы можете использовать функцию `explore`, чтобы возвратить список кубов, измерений и элементов для использования при создании запроса. Это удобно, когда у вас нет доступа к другим средствам просмотра OLAP либо требуется создать запрос многомерных выражений или управлять им программно.

#### <a name="to-list-the-cubes-available-on-the-specified-connection"></a>Вывод списка кубов, доступных в указанном подключении

Чтобы просмотреть все кубы или перспективы для экземпляра, на просмотр которого у вас есть разрешение, укажите дескриптор в качестве аргумента `explore`.

> [!IMPORTANT]
> Окончательный результат — **не** куб; Значение TRUE указывает, что операция с метаданными выполнена успешно. Если аргументы недопустимы, возникает ошибка.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs <- OlapConnection(cnnstr)
explore(ocs)
```

| Результаты  |
| ----|
| _Учебник по службам Analysis Services_|
|_Продажи через Интернет_|
|_Товарооборот посредников_|
|_Сводка продаж_|
|_[1] TRUE_|

#### <a name="to-get-a-list-of-cube-dimensions"></a>Получение списка измерений куба

Чтобы просмотреть все измерения куба или перспективы, укажите имя куба или перспективы.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs \<- OlapConnection(cnnstr)
explore(ocs, "Sales")
```

| Результаты  |
| ----|
| _Заказчик_|
|_Дата_|
|_Регион_|


#### <a name="to-return-all-members-of-the-specified-dimension-and-hierarchy"></a>Возврат всех элементов заданного измерения и иерархии

После определения источника и создания дескриптора укажите куб, измерение и иерархию для возврата. В результатах возврата элементы с **->** префиксом представляют потомки предыдущего элемента.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs <- OlapConnection(cnnstr)
explore(ocs, "Analysis Services Tutorial", "Product", "Product Categories", "Category")
```

| Результаты  |
| ----|
| _Accessories_|
|_Bikes_|
|_Clothing_|
|_Components_|
|-> Компоненты сборки|
|-> Компоненты сборки|


## <a name="see-also"></a>См. также

[Использование данных из кубов OLAP в R](../../advanced-analytics/r/using-data-from-olap-cubes-in-r.md)
