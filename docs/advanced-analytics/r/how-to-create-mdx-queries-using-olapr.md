---
title: Создание многомерных Выражений запросов на языке R, с помощью olapR в машинного обучения SQL Server | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7fe2749e6f70522fbd010d5af78890dfe897426b
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51696933"
---
# <a name="how-to-create-mdx-queries-in-r-using-olapr"></a>Создание запросов многомерных Выражений в R с помощью olapR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[OlapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) пакет поддерживает запросы многомерных Выражений для кубов, размещенные в SQL Server Analysis Services. Можно построить запрос к существующего куба, просмотра измерений и других объектов куба и вставьте в существующих запросах многомерных Выражений для извлечения данных.

В этой статье описываются два основных способа использования **olapR** пакета:

+ [Создать запрос многомерных Выражений из R, с помощью конструкторов, предоставленных в olapR пакета](#buildMDX)
+ [Выполните существующих, допустимые MDX-запрос с помощью olapR и поставщик данных для КУБА](#executeMDX)

Не поддерживаются следующие операции:

+ Запросов DAX в табличной модели
+ Создание новых объектов OLAP
+ Обратная запись для секций, включая меры или суммы

## <a name="buildMDX"></a> Создать запрос многомерных Выражений из R

1. Определите строку подключения, указывающую источник данных OLAP (экземпляр служб SQL Server Analysis Services ) и поставщик MSOLAP.

2. Используйте функцию `OlapConnection(connectionString)` , чтобы создать дескриптор для запроса многомерных выражений и передать строку подключения.

3. Используйте конструктор `Query()` для создания экземпляра объекта запроса.

4. Используйте следующие вспомогательные функции, чтобы предоставить дополнительные сведения об измерениях и мерах для включения в запрос многомерных выражений:

     + `cube()` Укажите имя базы данных SSAS. При подключении к именованному экземпляру, укажите имя компьютера и имя экземпляра. 
     + `columns()` Укажите имена мер для использования в **ON COLUMNS** аргумент.
     + `rows()` Укажите имена мер для использования в **ON ROWS** аргумент.
     + `slicers()` Укажите поле или элементы для использования в качестве среза. Срез аналогичен фильтру, который применяется ко всем данным запроса многомерных выражений.
     
     + `axis()` Укажите имя дополнительной оси для использования в запросе. 
     
         Куб OLAP может содержать до 128 осей запроса. Как правило, первые четыре оси, называются **столбцы**, **строк**, **страниц**, и **главы**. 
         
         Если запрос относительно прост, для его создания можно использовать функции `columns`, `rows`и т. п. Однако можно также использовать функцию `axis()` с ненулевым значением индекса для создания запроса многомерных выражений с несколькими квалификаторами или для добавления дополнительных измерений в качестве квалификаторов.

5. Передайте дескриптор и готовый запрос многомерных Выражений, в одну из следующих функций, в зависимости от вида результатов: 

  + `executeMD` возвращает многомерный массив.
  + `execute2D` возвращает двухмерный (табличный) кадр данных.

## <a name="executeMDX"></a> Выполнить допустимый запрос многомерных Выражений из R

1. Определите строку подключения, указывающую источник данных OLAP (экземпляр служб SQL Server Analysis Services ) и поставщик MSOLAP.

2. Используйте функцию `OlapConnection(connectionString)` , чтобы создать дескриптор для запроса многомерных выражений и передать строку подключения.

3. Определите переменную R для хранения текста запроса многомерных выражений.

4. Передайте дескриптор и переменную, содержащую запрос многомерных выражений, в функции `executeMD` или `execute2D`в зависимости от вида результатов.

    + `executeMD` возвращает многомерный массив.
    + `execute2D` возвращает двухмерный (табличный) кадр данных.

## <a name="examples"></a>Примеры

Следующие примеры основаны на данных киоска и куба проекта AdventureWorks, так как этот проект является широко доступны в нескольких версиях, включая файлы резервных копий, которые могут быть легко возвращены к службам Analysis Services. Если у вас нет существующего куба, получите образец куба при помощи любого из этих параметров:

+ Создать куб, который используется в этих примерах, выполнив учебник по службам Analysis Services вплоть до занятия 4: [создание куба OLAP](../../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)

+ Скачать существующий куб в качестве резервной копии и восстановить его на экземпляре служб Analysis Services. Например, этот узел содержит полностью обработанный куб в формате ZIP: [2014 SQL многомерной модели Adventure Works](https://msftdbprodsamples.codeplex.com/downloads/get/882334). Извлеките файл, а затем восстановите его в своем экземпляр SSAS. Дополнительные сведения см. в разделе [резервного копирования и восстановления](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md), или [командлет Restore-ASDatabase](../../analysis-services/powershell/restore-asdatabase-cmdlet.md).

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
+ Этот запрос возвращает таблицу с тремя столбцами, содержащую _Свертка_ Сводка продаж через Интернет из любой страны.
+ В предложении WHERE указано _ось среза_. В этом примере срез использует элементы **SalesTerritory** измерения для фильтрации запроса, чтобы в вычислениях использовались только данные по продажам из Австралии.

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

Для именованного экземпляра не забудьте экранировать все символы, которые можно считать управляющие символы в R.  Например следующая строка подключения ссылается на экземпляр OLAP01, на сервере с именем ContosoHQ:

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

Если определить запрос с помощью построителя многомерных Выражений в SQL Server Management Studio и затем сохранить строку многомерного Выражения, он будет число осей, начиная с 0, как показано ниже: 

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[Internet Sales-Sales Amount]} ON AXIS(0), 
   {[Product].[Product Line].[Product Line].MEMBERS} ON AXIS(1) 
   FROM [Analysis Services Tutorial] 
   WHERE [Sales Territory].[Sales Territory Countr,y].[Australia]
```

При этом данный запрос все равно можно выполнить в качестве заранее определенной строки многомерного выражения. Тем не менее для создания того же запроса с помощью R с помощью `axis()` функции, можно изменить осей, начиная с 1.

### <a name="2-explore-cubes-and-their-fields-on-an-ssas-instance"></a>2. Просмотр кубов и их полей в экземпляре SSAS

Вы можете использовать функцию `explore`, чтобы возвратить список кубов, измерений и элементов для использования при создании запроса. Это удобно, когда у вас нет доступа к другим средствам просмотра OLAP либо требуется создать запрос многомерных выражений или управлять им программно.

#### <a name="to-list-the-cubes-available-on-the-specified-connection"></a>Вывод списка кубов, доступных в указанном подключении

Чтобы просмотреть все кубы или перспективы для экземпляра, на просмотр которого у вас есть разрешение, укажите дескриптор в качестве аргумента `explore`.

> [!IMPORTANT]
> Конечным результатом является **не** куба; TRUE просто означает, что операция с метаданными выполнена успешно. Если аргументы недопустимы, возникает ошибка.

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

После определения источника и создания дескриптора укажите куб, измерение и иерархию для возврата. В возвращаемых результатах, элементы, которые начинаются с префикса **->** представляют потомков предыдущего элемента.

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


## <a name="see-also"></a>См. также

[Использование данных из кубов OLAP в R](../../advanced-analytics/r/using-data-from-olap-cubes-in-r.md)
