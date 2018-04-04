---
title: Как для создания Многомерных запросов, с помощью olapR | Документы Microsoft
ms.custom: ''
ms.date: 11/29/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: 9d917316a9d25b0634605e0f55eae3eda93f8669
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="how-to-create-mdx-queries-using-olapr"></a>Создание запросов многомерных Выражений, с помощью olapR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[OlapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) пакет поддерживает запросы многомерных Выражений в кубах, размещенные в SQL Server Analysis Services. Можно построить запрос к существующего куба, просмотра измерений и других объектов куба и вставьте в существующих запросах многомерных Выражений для получения данных.

В этой статье описывается два основных областей применения **olapR** пакета:

+ [Создать запрос многомерных Выражений из R, с помощью конструкторов, предоставленных в пакете olapR](#buildMDX)
+ [Выполнение существующего, допустимые запроса многомерных Выражений с помощью olapR и поставщик данных для КУБА](#executeMDX)

Не поддерживаются следующие операции:

+ Запросы DAX для табличной модели
+ Создание новых объектов OLAP
+ Обратная запись для секций, включая меры или суммы

## <a name="buildMDX"></a> Создать запрос многомерных Выражений из R

1. Определите строку подключения, указывающую источник данных OLAP (экземпляр служб SQL Server Analysis Services ) и поставщик MSOLAP.

2. Используйте функцию `OlapConnection(connectionString)` , чтобы создать дескриптор для запроса многомерных выражений и передать строку подключения.

3. Используйте конструктор `Query()` для создания экземпляра объекта запроса.

4. Используйте следующие вспомогательные функции, чтобы предоставить дополнительные сведения об измерениях и мерах для включения в запрос многомерных выражений:

     + `cube()` Укажите имя базы данных SSAS. При соединении с именованным экземпляром введите имя компьютера и имя экземпляра. 
     + `columns()` Укажите имена мер для использования в **СТОЛБЦЫ ON** аргумент.
     + `rows()` Укажите имена мер для использования в **СТРОК ON** аргумент.
     + `slicers()` Укажите поле или элементы для использования в качестве среза. Срез аналогичен фильтру, который применяется ко всем данным запроса многомерных выражений.
     
     + `axis()` Укажите имя дополнительной оси для использования в запросе. 
     
         Куб OLAP может содержать до 128 осей запроса. Как правило, первые четыре оси, называются **столбцы**, **строк**, **страниц**, и **главах**. 
         
         Если запрос относительно прост, для его создания можно использовать функции `columns`, `rows`и т. п. Однако можно также использовать функцию `axis()` с ненулевым значением индекса для создания запроса многомерных выражений с несколькими квалификаторами или для добавления дополнительных измерений в качестве квалификаторов.

5. Передайте дескриптор и завершенным запросом многомерных Выражений, в одну из следующих функций, в зависимости от форму результатов: 

  + `executeMD` возвращает многомерный массив.
  + `execute2D` возвращает двухмерный (табличный) кадр данных.

## <a name="executeMDX"></a> Выполнение допустимый запрос многомерных Выражений из R

1. Определите строку подключения, указывающую источник данных OLAP (экземпляр служб SQL Server Analysis Services ) и поставщик MSOLAP.

2. Используйте функцию `OlapConnection(connectionString)` , чтобы создать дескриптор для запроса многомерных выражений и передать строку подключения.

3. Определите переменную R для хранения текста запроса многомерных выражений.

4. Передайте дескриптор и переменную, содержащую запрос многомерных выражений, в функции `executeMD` или `execute2D`в зависимости от вида результатов.

    + `executeMD` возвращает многомерный массив.
    + `execute2D` возвращает двухмерный (табличный) кадр данных.

## <a name="examples"></a>Примеры

Следующие примеры основаны на данных киоска и куба проекта AdventureWorks, так как этот проект является широко доступны в нескольких версиях, включая файлы резервной копии, которые могут быть легко восстановлены к службам Analysis Services. Если у вас нет существующего куба, получите образец куба с использованием любого из этих параметров:

+ Создать куб, который используется в этих примерах ниже учебника служб Analysis Services до занятия 4: [создание куба OLAP](../../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)

+ Загрузка существующего куба в резервную копию и восстановить его с экземпляром служб Analysis Services. Например, на этом сайте предоставлена полностью обработанный куб в сжатый формат: [2014 SQL многомерной модели Adventure Works](http://msftdbprodsamples.codeplex.com/downloads/get/882334). Извлеките файл, а затем восстановите его на свой экземпляр SSAS. Дополнительные сведения см. в разделе [резервного копирования и восстановления](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md), или [командлета Restore-ASDatabase](../../analysis-services/powershell/restore-asdatabase-cmdlet.md).

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
+ Этот запрос возвращает таблицу с тремя столбцами, содержащий _свертки_ Сводка по продажам через Интернет из любой страны.
+ Предложение WHERE определяет _ось среза_. В этом примере срез использует членом **SalesTerritory** измерений для фильтрации запроса, чтобы только данные по продажам из Австралии, используемых в вычислениях.

#### <a name="to-build-this-query-using-the-functions-provided-in-olapr"></a>Создание этого запроса с помощью функций, предоставленных в olapR

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs <- OlapConnection(cnnstr)

qry <- Query()
cube(qry) <- "[Analysis Services Tutorial]"
columns(qry) <- c("[Measures].[Internet Sales Count]", "[Measures].[Internet Sales-Sales Amount]")
rows(qry) <- c("[Product].[Product Line].[Product Line].MEMBERS") 
slicers(qry) <- c("[Sales Territory].[Sales Territory Country].[Australia]")

result1 <- executeMD(ocs, qry)

```

Для именованного экземпляра убедитесь, что escape-символы, может считаться управляющие символы в R.  Например следующая строка подключения ссылается на экземпляр OLAP01, на сервере с именем ContosoHQ:

```R
cnnstr <- "Data Source=ContosoHQ\\OLAP01; Provider=MSOLAP;"
```

#### <a name="to-run-this-query-as-a-predefined-mdx-string"></a>Выполнение этого запроса в качестве заранее определенной строки многомерного выражения

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs <- OlapConnection(cnnstr)

mdx <- "SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, {[Product].[Product Line].[Product Line].MEMBERS} ON ROWS FROM [Analysis Services Tutorial] WHERE [Sales Territory].[Sales Territory Country].[Australia]"

result2 <- execute2D(ocs, mdx)
```

Если определить запрос, используя построитель многомерных Выражений в SQL Server Management Studio и затем сохраните строку многомерного Выражения, оно будет число осей, начиная с 0, как показано ниже: 

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[Internet Sales-Sales Amount]} ON AXIS(0), 
   {[Product].[Product Line].[Product Line].MEMBERS} ON AXIS(1) 
   FROM [Analysis Services Tutorial] 
   WHERE [Sales Territory].[Sales Territory Countr,y].[Australia]
```

При этом данный запрос все равно можно выполнить в качестве заранее определенной строки многомерного выражения. Тем не менее для создания того же запроса, с помощью R с помощью `axis()` функции, можно изменить осей, начиная с 1.

### <a name="2-explore-cubes-and-their-fields-on-an-ssas-instance"></a>2. Просмотр кубов и их полей в экземпляре SSAS

Вы можете использовать функцию `explore`, чтобы возвратить список кубов, измерений и элементов для использования при создании запроса. Это удобно, когда у вас нет доступа к другим средствам просмотра OLAP либо требуется создать запрос многомерных выражений или управлять им программно.

#### <a name="to-list-the-cubes-available-on-the-specified-connection"></a>Вывод списка кубов, доступных в указанном подключении

Чтобы просмотреть все кубы или перспективы для экземпляра, на просмотр которого у вас есть разрешение, укажите дескриптор в качестве аргумента `explore`.

> [!IMPORTANT]
> Окончательный результат **не** куба; Значение TRUE означает просто, метаданные операция выполнена успешно. Если аргументы недопустимы, возникает ошибка.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
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
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs \<- OlapConnection(cnnstr)
explore(ocs, "Sales")
```

| Результаты  |
| ----|
| _Заказчик_|
|_Дата_|
|_Регион_|


#### <a name="to-return-all-members-of-the-specified-dimension-and-hierarchy"></a>Возврат всех элементов заданного измерения и иерархии

После определения источника и создания дескриптора укажите куб, измерение и иерархию для возврата. В результаты, возвращаемые, элементы, которые начинаются с префикса **->** представляют потомков предыдущего элемента.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs \<- OlapConnection(cnnstr)
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


## <a name="see-also"></a>См. также:

[Используя данные из кубов OLAP в R](../../advanced-analytics/r/using-data-from-olap-cubes-in-r.md)
