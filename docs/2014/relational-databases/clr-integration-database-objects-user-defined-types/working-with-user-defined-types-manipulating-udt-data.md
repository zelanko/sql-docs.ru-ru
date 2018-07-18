---
title: Обработка данных определяемого пользователем ТИПА | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- CAST function
- data deletions [CLR integration]
- data insertions [CLR integration]
- CONVERT function
- data updates [CLR integration]
- comparing data
- updating data [CLR integration]
- removing data
- IsByteOrdered property
- variables [CLR integration]
- data manipulation [CLR integration]
- user-defined types [CLR integration], data manipulation
- deleting data
- UDTs [CLR integration], data manipulation
- invoking UDT methods
- inserting data
ms.assetid: 51b1a5f2-7591-4e11-bfe2-d88e0836403f
caps.latest.revision: 14
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b9d8d594b60b5e9ed9716d8aa3c0eed322db98fd
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37349896"
---
# <a name="manipulating-udt-data"></a>Работа с данными определяемого пользователем типа
  В [!INCLUDE[tsql](../../includes/tsql-md.md)] не используется специальный синтаксис для инструкций INSERT, UPDATE или DELETE при изменении данных в столбцах определяемого пользователем типа. Функции [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST и CONVERT используются для приведения собственных типов данных к определяемому пользователем типу.  
  
## <a name="inserting-data-in-a-udt-column"></a>Вставка данных в столбец определяемого пользователем типа  
 Следующие [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций вставки трех строк образца данных в **точек** таблицы. **Точки** тип данных состоит из X и Y целочисленных значений, которые представлены как свойства определяемого пользователем типа. Необходимо использовать функцию CAST или CONVERT привести разделяемые запятой значения X и Y к **точки** типа. Первые две инструкции используют функцию CONVERT для преобразования строкового значения **точки** типа, а третья инструкция использует функцию CAST:  
  
```  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '3,4'));  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '1,5'));  
INSERT INTO dbo.Points (PointValue) VALUES (CAST ('1,99' AS Point));  
```  
  
## <a name="selecting-data"></a>Выбор данных  
 Следующая инструкция SELECT выбирает двоичное значение определяемого пользователем типа.  
  
```  
SELECT ID, PointValue FROM dbo.Points  
```  
  
 Чтобы просмотреть выходные данных в удобном для чтения формате, вызовите `ToString` метод **точки** определяемого пользователем ТИПА, который преобразует значение в строковое представление.  
  
```  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points;  
```  
  
 Получены следующие результаты.  
  
```  
IDPointValue  
----------  
13,4  
21,5  
31,99  
```  
  
 Чтобы получить аналогичные результаты можно использовать функции [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST и CONVERT.  
  
```  
SELECT ID, CAST(PointValue AS varchar)   
FROM dbo.Points;  
  
SELECT ID, CONVERT(varchar, PointValue)   
FROM dbo.Points;  
```  
  
 **Точки** определяемого пользователем ТИПА предоставляет его координаты X и Y в виде свойств, которые можно выбрать по отдельности. Следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] выбирает координаты X и Y отдельно:  
  
```  
SELECT ID, PointValue.X AS xVal, PointValue.Y AS yVal   
FROM dbo.Points;  
```  
  
 Свойства X и Y возвращают целочисленные значения, которые отображаются в результирующем наборе.  
  
```  
IDxValyVal  
----------  
134  
215  
3199  
```  
  
## <a name="working-with-variables"></a>Работа с переменными  
 Можно также работать с переменными с помощью инструкции DECLARE, чтобы присвоить значение переменной определяемому пользователем типу. Следующие инструкции присваивают значение с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] SET и отображают результаты путем вызова метода `ToString` определяемого пользователем типа для переменной:  
  
```  
DECLARE @PointValue Point;  
SET @PointValue = (SELECT PointValue FROM dbo.Points  
    WHERE ID = 2);  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 Результирующий набор отображает значение переменной:  
  
```  
PointValue  
----------  
-1,5  
```  
  
 Следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] достигают такого же результата, используя инструкцию SELECT вместо SET, чтобы присвоить значение переменной:  
  
```  
DECLARE @PointValue Point;  
SELECT @PointValue = PointValue FROM dbo.Points  
    WHERE ID = 2;  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 Различие между использованием инструкций SELECT и SET для присваиваний значений переменных состоит в том, что SELECT позволяет присваивать значения нескольких переменных в одной инструкции SELECT, в то время как синтаксис SET требует для каждого присваивания переменной отдельной инструкции SET.  
  
## <a name="comparing-data"></a>Сравнение данных  
 Можно использовать операторы сравнения, чтобы сравнить значения в определяемом пользователем типе, если при определении класса для свойства `IsByteOrdered` задано значение `true`. Дополнительные сведения см. в разделе [Создание определяемого пользователем типа](creating-user-defined-types.md).  
  
```  
SELECT ID, PointValue.ToString() AS Points   
FROM dbo.Points  
WHERE PointValue > CONVERT(Point, '2,2');  
```  
  
 Можно сравнить внутренние значения определяемого пользователем типа независимо от значения свойства `IsByteOrdered`, если значения сами по себе сравнимы. Следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] выбирает строки, в которых X больше, чем Y:  
  
```  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points  
WHERE PointValue.X < PointValue.Y;  
```  
  
 Можно также использовать операторы сравнения с переменными, как показано в данном запросе, который ищет совпадения с PointValue.  
  
```  
DECLARE @ComparePoint Point;  
SET @ComparePoint = CONVERT(Point, '3,4');  
SELECT ID, PointValue.ToString() AS MatchingPoint   
FROM dbo.Points  
WHERE PointValue = @ComparePoint;  
```  
  
## <a name="invoking-udt-methods"></a>Вызов методов определяемого пользователем типа  
 Можно также вызывать методы, которые определены в определяемом пользователем типе [!INCLUDE[tsql](../../includes/tsql-md.md)]. **Точки** содержит три метода `Distance`, `DistanceFrom`, и `DistanceFromXY`. Примеры кода, определяющего эти три метода, см. в разделе [программирование определяемых пользователем типов](creating-user-defined-types-coding.md).  
  
 Следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] вызывает метод `PointValue.Distance`:  
  
```  
SELECT ID, PointValue.X AS [Point.X],   
    PointValue.Y AS [Point.Y],  
    PointValue.Distance() AS DistanceFromZero   
FROM dbo.Points;  
```  
  
 Результаты отображаются в `Distance` столбца:  
  
```  
IDXYDistance  
------------------------  
1345  
2155.09901951359278  
319999.0050503762308  
```  
  
 `DistanceFrom` Метод принимает аргумент **точки** тип данных и отображает расстояние от указанной точки до PointValue:  
  
```  
SELECT ID, PointValue.ToString() AS Pnt,  
   PointValue.DistanceFrom(CONVERT(Point, '1,99')) AS DistanceFromPoint  
FROM dbo.Points;  
```  
  
 Отображаются результаты работы метода `DistanceFrom` для каждой строки таблицы:  
  
```  
ID PntDistanceFromPoint  
---------------------  
13,495.0210502993942  
21,594  
31,990  
```  
  
 Метод `DistanceFromXY` принимает в качестве аргументов отдельно две точки:  
  
```  
SELECT ID, PointValue.X as X, PointValue.Y as Y,   
PointValue.DistanceFromXY(1, 99) AS DistanceFromXY   
FROM dbo.Points  
```  
  
 Результирующий набор аналогичен результату работы метода `DistanceFrom`.  
  
## <a name="updating-data-in-a-udt-column"></a>Обновление данных в столбце определяемого пользователем типа  
 Чтобы обновлять данные в столбце определяемого пользователем типа, используется инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE. Также можно использовать метод определяемого пользователем типа, чтобы обновить состояние объекта. Следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] обновляет одну строку в таблице:  
  
```  
UPDATE dbo.Points  
SET PointValue = CAST('1,88' AS Point)  
WHERE ID = 3  
```  
  
 Также можно обновлять элементы определяемого пользователем типа отдельно. Следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] обновляет только координату Y:  
  
```  
UPDATE dbo.Points  
SET PointValue.Y = 99  
WHERE ID = 3  
```  
  
 Если определяемый пользователем тип был определен с упорядочением байт, установленным в значение `true`, [!INCLUDE[tsql](../../includes/tsql-md.md)] может оценить столбец определяемого пользователем типа в предложении WHERE.  
  
```  
UPDATE dbo.Points  
SET PointValue = '4,5'  
WHERE PointValue = '3,4';  
```  
  
### <a name="updating-limitations"></a>Ограничения обновлений  
 Нельзя обновить несколько свойств за раз с помощью инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)]. Например, следующая инструкция UPDATE выполняется с ошибкой, так как нельзя использовать одно и то же имя столбца дважды в одной инструкции UDATE.  
  
```  
UPDATE dbo.Points  
SET PointValue.X = 5, PointValue.Y = 99  
WHERE ID = 3  
```  
  
 Чтобы обновить каждую точку отдельно, необходимо создать метод мутатора в сборке определяемого пользователем типа Point. Можно затем обратиться к методу мутатора в инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE для обновления объекта, как показано ниже:  
  
```  
UPDATE dbo.Points  
SET PointValue.SetXY(5, 99)  
WHERE ID = 3  
```  
  
## <a name="deleting-data-in-a-udt-column"></a>Удаление данных из столбца определяемого пользователем типа  
 Чтобы удалить данные в определяемом пользователем типе, используется инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE. Следующая инструкция удаляет все строки из таблицы, которые удовлетворяют критерию, указанному в предложении WHERE. Если предложение WHERE пропущено в инструкции DELETE, будут удалены все строки таблицы.  
  
```  
DELETE FROM dbo.Points  
WHERE PointValue = CAST('1,99' AS Point)  
```  
  
 Инструкция UPDATE используется, если необходимо удалить значения в столбце определяемого пользователем типа и оставить другие значения строки без изменений. Этот пример задает столбцу PointValue значение NULL.  
  
```  
UPDATE dbo.Points  
SET PointValue = null  
WHERE ID = 2  
```  
  
## <a name="see-also"></a>См. также  
 [Работа с определяемыми пользователем типами в SQL Server](working-with-user-defined-types-in-sql-server.md)  
  
  
