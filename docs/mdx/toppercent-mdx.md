---
title: TopPercent (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- TOPPERCENT
dev_langs:
- kbMDX
helpviewer_keywords:
- TopPercent function
ms.assetid: a40cfbb8-5bf4-4ae2-8686-df9a07206d56
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 6e8ca7e44a8138ab097a9f7a486f4e76aca30415
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="toppercent-mdx"></a>TopPercent (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Сортирует набор в убывающем порядке и возвращает набор кортежей с наибольшими значениями, совокупное значение которых равно указанному проценту или больше него.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TopPercent(Set_Expression, Percentage, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Процент*  
 Допустимое числовое выражение, указывающее процент возвращаемых кортежей.  
  
> [!IMPORTANT]  
>  *Процент* должно быть положительное значение; отрицательные значения вызывают ошибку.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Замечания  
 **TopPercent** функция вычисляет сумму указанного числового выражения, вычисленное на указанного набора, отсортированного в убывающем порядке. Затем функция возвращает элементы с наибольшими значениями, доля суммы которых в суммарном значении меньше указанного процента или равна ему. Эта функция возвращает самый маленький поднабор набора, совокупное значение которого равно по меньшей мере заданному проценту. Возвращенные элементы упорядочены по убыванию.  
  
> [!WARNING]  
>  Если *Numeric_Expression* возвращает любое отрицательное значение затем **TopPercent** возвращает по строке только один (1).  
>   
>  Подробное представление такой особенности см. во втором примере.  
  
> [!IMPORTANT]  
>  Как [BottomPercent](../mdx/bottompercent-mdx.md) функции **TopPercent** функция всегда нарушает иерархию.  
  
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
  
||Reseller Sales Amount|  
|-|---------------------------|  
|Toronto|$3,508,904.84|  
|London|$1,521,530.09|  
|Seattle|$1,209,418.16|  
|Париж|$1,170,425.18|  
  
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
 Следующее пошаговое руководство поможет понять, как влияет отрицательных значений в *Numeric_Expression*. Сначала нужно построить контекст, где представлен этот эффект.  
  
 Следующий запрос возвращает таблицу со столбцами «Sales Amount», «Total Product Cost» и «Gross Profit» для посредников с сортировкой по убыванию прибыли. Заметьте, что для прибыли заданы только отрицательные значения, поэтому сверху будет отображаться минимальный убыток.  
  
```  
SELECT { [Measures].[Reseller Sales Amount], [Measures].[Reseller Total Product Cost], [Measures].[Reseller Gross Profit] } ON columns  
     ,  ORDER( [Product].[Product Categories].[Bikes].[Touring Bikes].children, [Measures].[Reseller Gross Profit], BDESC )   ON rows  
FROM [Adventure Works]  
  
```  
  
 Этот запрос возвращает следующие результаты. Средние строки удалены для упрощения чтения.  
  
||Reseller Sales Amount|Reseller Total Product Cost|Reseller Gross Profit|  
|-|---------------------------|---------------------------------|---------------------------|  
|Touring-2000 Blue, 50|$157,444.56|$163,112.57|($5,668.01)|  
|Синий, 46 Touring-2000|$321,027.03|$333,021.50|($11,994.47)|  
|Синий, 62 Touring-3000|$87,773.61|$100,133.52|($12,359.91)|  
|…|…|…|…|  
|Желтый, 46 Touring-1000|$1,016,312.83|$1,234,454.27|($218,141.44)|  
|Touring-1000 Yellow, 60|$1,184,363.30|$1,443,407.51|($259,044.21)|  
  
 Если нужно представить первые 100 % велосипедов по прибыльности, следует составить следующий запрос:  
  
```  
SELECT { [Measures].[Reseller Sales Amount], [Measures].[Reseller Total Product Cost], [Measures].[Reseller Gross Profit] } ON columns  
     ,  TOPPERCENT( [Product].[Product Categories].[Bikes].[Touring Bikes].children, 100,[Measures].[Reseller Gross Profit] )   ON rows  
FROM [Adventure Works]  
  
```  
  
 Заметьте, что в запросе указан размер выборки 100 % и должны возвращаться все строки. Тем не менее так как отрицательные значения *Numeric_Expression* , возвращается только одна строка.  
  
||Reseller Sales Amount|Reseller Total Product Cost|Reseller Gross Profit|  
|-|---------------------------|---------------------------------|---------------------------|  
|Touring-2000 Blue, 50|$157,444.56|$163,112.57|($5,668.01)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
