---
description: TopPercent (многомерные выражения)
title: TopPercent (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5f0ae1e59a46c03300018f3243926bb30cef0398
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412869"
---
# <a name="toppercent-mdx"></a>TopPercent (многомерные выражения)


  Сортирует набор в убывающем порядке и возвращает набор кортежей с наибольшими значениями, совокупное значение которых равно указанному проценту или больше него.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TopPercent(Set_Expression, Percentage, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Percentage*  
 Допустимое числовое выражение, указывающее процент возвращаемых кортежей.  
  
> [!IMPORTANT]  
>  *Процент*  должен быть положительным значением; отрицательные значения вызывают ошибку.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Remarks  
 Функция **TopPercent** вычисляет сумму указанного числового выражения, вычисленного для указанного набора, отсортированного в порядке убывания. Затем функция возвращает элементы с наибольшими значениями, доля суммы которых в суммарном значении меньше указанного процента или равна ему. Эта функция возвращает самый маленький поднабор набора, совокупное значение которого равно по меньшей мере заданному проценту. Возвращенные элементы упорядочены по убыванию.  
  
> [!WARNING]  
>  Если *Numeric_Expression*  возвращает любое отрицательное значение, **TopPercent** возвращает только одну (1) строку.  
>   
>  Подробное представление такой особенности см. во втором примере.  
  
> [!IMPORTANT]  
>  Как и функция [BottomPercent](../mdx/bottompercent-mdx.md) , функция **TopPercent** всегда прерывает иерархию.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращаются лучшие города, дающие вклад в 10 % от продаж посредников в категории Bike. Результат сортируется по убыванию, начиная с города с максимальной суммой продаж.  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopPercent  
   ({[Geography].[Geography].[City].Members}  
   , 10  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].[Bikes])  
```  
  
 Приведенное выше выражение дает следующие результаты.  
  
|Город|Reseller Sales Amount|  
|-|---------------------------|  
|Toronto|$3 508 904,84|  
|London|$1 521 530,09|  
|Seattle|$1 209 418,16|  
|Париж|$1 170 425,18|  
  
 Исходный набор данных можно получить следующим запросом, возвращающим 588 строк:  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
Order  
   ({[Geography].[Geography].[City].Members}  
   , [Measures].[Reseller Sales Amount]  
   , BDESC  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].[Bikes])  
  
```  
  
## <a name="example"></a>Пример  
 Следующее пошаговое руководство поможет понять последствия отрицательных значений в *Numeric_Expression*. Сначала нужно построить контекст, где представлен этот эффект.  
  
 Следующий запрос возвращает таблицу со столбцами «Sales Amount», «Total Product Cost» и «Gross Profit» для посредников с сортировкой по убыванию прибыли. Заметьте, что для прибыли заданы только отрицательные значения, поэтому сверху будет отображаться минимальный убыток.  
  
```  
SELECT { [Measures].[Reseller Sales Amount], [Measures].[Reseller Total Product Cost], [Measures].[Reseller Gross Profit] } ON columns  
     ,  ORDER( [Product].[Product Categories].[Bikes].[Touring Bikes].children, [Measures].[Reseller Gross Profit], BDESC )   ON rows  
FROM [Adventure Works]  
  
```  
  
 Этот запрос возвращает следующие результаты. Средние строки удалены для упрощения чтения.  
  
|Туристические велосипеды|Reseller Sales Amount|Reseller Total Product Cost|Reseller Gross Profit|  
|-|---------------------------|---------------------------------|---------------------------|  
|Touring-2000 Blue, 50|$157 444,56|$163 112,57|($5 668,01)|  
|Обзор — 2000 синий, 46|$321 027,03|$333 021,50|($11 994,47)|  
|Обзор — 3000 синий, 62|$87 773,61|$100 133,52|($12 359,91)|  
|...|...|...|...|  
|Обзор — 1000 желтый, 46|$1 016 312,83|$1 234 454,27|($218 141,44)|  
|Touring-1000 Yellow, 60|$1 184 363,30|$1 443 407,51|($259 044,21)|  
  
 Если нужно представить первые 100 % велосипедов по прибыльности, следует составить следующий запрос:  
  
```  
SELECT { [Measures].[Reseller Sales Amount], [Measures].[Reseller Total Product Cost], [Measures].[Reseller Gross Profit] } ON columns  
     ,  TOPPERCENT( [Product].[Product Categories].[Bikes].[Touring Bikes].children, 100,[Measures].[Reseller Gross Profit] )   ON rows  
FROM [Adventure Works]  
  
```  
  
 Заметьте, что в запросе указан размер выборки 100 % и должны возвращаться все строки. Однако, поскольку в *Numeric_Expression* есть отрицательные значения, возвращается только одна строка.  
  
|Туристические велосипеды|Reseller Sales Amount|Reseller Total Product Cost|Reseller Gross Profit|  
|-|---------------------------|---------------------------------|---------------------------|  
|Touring-2000 Blue, 50|$157 444,56|$163 112,57|($5 668,01)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
