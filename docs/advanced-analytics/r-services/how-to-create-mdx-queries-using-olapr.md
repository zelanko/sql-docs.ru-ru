---
title: "Создание запросов многомерных выражений с помощью olapR | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: c12b988e-be7e-41ba-a84c-299a5c45d4ab
caps.latest.revision: 3
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 3
---
# Создание запросов многомерных выражений с помощью olapR
## <a name="how-to-build-an-mdx-query-from-r"></a>Создание запроса многомерных выражений из R

1. Определите строку подключения, указывающую источник данных OLAP (экземпляр служб SQL Server Analysis Services ) и поставщик MSOLAP.

2. Используйте функцию `OlapConnection(connectionString)`, чтобы создать дескриптор для запроса многомерных выражений и передать строку подключения.

3. Используйте конструктор `Query()` для создания экземпляра объекта запроса.

4. Используйте следующие вспомогательные функции, чтобы предоставить дополнительные сведения об измерениях и мерах для включения в запрос многомерных выражений:
     + `cube()` Укажите имя базы данных SSAS.
     + `columns()` Укажите имена мер для использования в аргументе ON COLUMNS.  
     + `rows()` Укажите имена мер для использования в аргументе ON ROWS.
     + `slicers()` Укажите поле или элементы для использования в качестве среза. Срез аналогичен фильтру, который применяется ко всем данным запроса многомерных выражений.
     
     + `axis()` Укажите имя дополнительной оси для использования в запросе. Куб OLAP может содержать до 128 осей запроса. Обычно первые четыре оси обозначают столбцы, строки, страницы и главы. Если запрос относительно прост, для его создания можно использовать функции `columns`, `rows` и т. п.     
     Однако можно также использовать функцию `axis()` с ненулевым значением индекса для создания запроса многомерных выражений с несколькими квалификаторами или для добавления дополнительных измерений в качестве квалификаторов.

5. Передайте дескриптор и готовый запрос многомерных выражений в функции `executeMD` или `execute2D` в зависимости от вида результатов.

  + `executeMD` возвращает многомерный массив.
  + `execute2D` возвращает двухмерный (табличный) кадр данных.


## <a name="how-to-run-an-existing-mdx-query-from-r"></a>Запуск существующего запроса многомерных выражений из R

1. Определите строку подключения, указывающую источник данных OLAP (экземпляр служб SQL Server Analysis Services ) и поставщик MSOLAP.

2. Используйте функцию `OlapConnection(connectionString)`, чтобы создать дескриптор для запроса многомерных выражений и передать строку подключения.

3. Определите переменную R для хранения текста запроса многомерных выражений.

4. Передайте дескриптор и переменную, содержащую запрос многомерных выражений, в функции `executeMD` или `execute2D` в зависимости от вида результатов.

    + `executeMD` возвращает многомерный массив.
    + `execute2D` возвращает двухмерный (табличный) кадр данных.



## <a name="examples"></a>Примеры

### <a name="1-basic-mdx-with-slicer"></a>1. Базовое многомерное выражение со срезом

Этот запрос многомерных выражений выбирает _меры_ для количества и объема продаж через Интернет и размещает их на оси столбцов. Она добавляет элементы измерения SalesTerritory в качестве *среза* для фильтрации запроса, чтобы в вычислениях использовались только данные по продажам из Австралии.

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, 
{[Product].[Product Line].[Product Line].MEMBERS} ON ROWS 
FROM [Analysis Services Tutorial] 
WHERE [Sales Territory].[Sales Territory Country].[Australia]
```

+ В столбцах можно указать несколько мер в виде элементов строки с разделителями-запятыми.
+ Ось строк использует все возможные значения (все элементы) измерения Product Line. 
+ Этот запрос возвращает таблицу с тремя столбцами, содержащую сводное _сведение_ по продажам через Интернет для всех стран. 
+ Предложение WHERE является _осью среза_. Этот срез использует элементы измерения SalesTerritory для фильтрации запроса, чтобы в вычислениях использовались только данные по продажам из Австралии.

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

#### <a name="to-run-this-query-as-a-predefined-mdx-string"></a>Выполнение этого запроса в качестве заранее определенной строки многомерного выражения

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs <- OlapConnection(cnnstr)

mdx <- "SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, {[Product].[Product Line].[Product Line].MEMBERS} ON ROWS FROM [Analysis Services Tutorial] WHERE [Sales Territory].[Sales Territory Country].[Australia]"

result2 <- execute2D(ocs, mdx)
```

Обратите внимание, что, если определить запрос с помощью построителя многомерных выражений в SQL Server Management Studio и затем сохранить строку многомерного выражения, номера его осей будут начинаться с 0, как показано ниже. 

~~~~
SELECT {[Measures].[Internet Sales Count], [Measures].[Internet Sales-Sales Amount]} ON AXIS(0), 
   {[Product].[Product Line].[Product Line].MEMBERS} ON AXIS(1) 
   FROM [Analysis Services Tutorial] 
   WHERE [Sales Territory].[Sales Territory Country].[Australia]
~~~~

При этом данный запрос все равно можно выполнить в качестве заранее определенной строки многомерного выражения. Однако для создания того же запроса в R с помощью функции `axis()` нужно убедиться, что номера осей начинаются с 1.


### <a name="2-explore-cubes-and-their-fields-on-an-ssas-instance"></a>2. Просмотр кубов и их полей в экземпляре SSAS

Вы можете использовать функцию `explore`, чтобы возвратить список кубов, измерений и элементов для использования при создании запроса. Это удобно, когда у вас нет доступа к другим средствам просмотра OLAP либо требуется создать запрос многомерных выражений или управлять им программно.

#### <a name="to-list-the-cubes-available-on-the-specified-connection"></a>Вывод списка кубов, доступных в указанном подключении

Чтобы просмотреть все кубы или перспективы для экземпляра, на просмотр которого у вас есть разрешение, укажите дескриптор в качестве аргумента `explore`.
Обратите внимание, что конечный результат не является кубом. Значение TRUE просто означает, что операция с метаданными выполнена успешно. Если аргументы недопустимы, возникает ошибка.

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
ocs <- OlapConnection(cnnstr)
explore(ocs, "Sales")
```

| Результаты  |  
| ----|
| _Заказчик_|
|_Дата_|
|_Регион_|


#### <a name="to-return-all-members-of-the-specified-dimension-and-hierarchy"></a>Возврат всех элементов заданного измерения и иерархии

После определения источника и создания дескриптора укажите куб, измерение и иерархию для возврата.
Обратите внимание, что элементы в возвращаемых результатах, имеющие префикс **->**, представляют потомков предыдущего элемента.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
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

[Использование данных из кубов OLAP в R](../../advanced-analytics/r-services/using-data-from-olap-cubes-in-r.md)