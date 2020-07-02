---
title: Управление данными определяемых пользователем типов | Документация Майкрософт
description: В этой статье описывается, как вставлять, выбирать и обновлять данные в столбцах определяемого пользователем типа базы данных SQL Server.
ms.custom: ''
ms.date: 12/05/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 17913dab743f1aaaa7672ce855aa85ce8434f3c0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727755"
---
# <a name="working-with-user-defined-types---manipulating-udt-data"></a>Работа с определяемыми пользователем типами — обработка данных определяемого пользователем типа
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В [!INCLUDE[tsql](../../includes/tsql-md.md)] не используется специальный синтаксис для инструкций INSERT, UPDATE или DELETE при изменении данных в столбцах определяемого пользователем типа. Функции [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST и CONVERT используются для приведения собственных типов данных к определяемому пользователем типу.  
  
## <a name="inserting-data-in-a-udt-column"></a>Вставка данных в столбец определяемого пользователем типа  
 Следующие [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции вставляют три строки образца данных в таблицу **points** . Тип данных **Point** состоит из целочисленных значений X и Y, которые предоставляются как свойства определяемого пользователем типа. Для приведения значений X и Y с разделителями-запятыми в тип **Point** необходимо использовать функцию CAST или Convert. Первые две инструкции используют функцию CONVERT для преобразования строкового значения в тип **Point** , а третья инструкция использует функцию CAST:  
  
```sql  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '3,4'));  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '1,5'));  
INSERT INTO dbo.Points (PointValue) VALUES (CAST ('1,99' AS Point));  
```  
  
## <a name="selecting-data"></a>Выбор данных  
 Следующая инструкция SELECT выбирает двоичное значение определяемого пользователем типа.  
  
```sql  
SELECT ID, PointValue FROM dbo.Points  
```  
  
 Чтобы просмотреть выходные данные в удобочитаемом формате, вызовите метод **ToString** определяемого пользователем типа **Point** , который преобразует значение в строковое представление.  
  
```sql  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points;  
```  
  
 Получены следующие результаты.  
  
```  
ID PointValue  
-- ----------  
 1 3,4  
 2 1,5  
 3 1,99  
```  
  
 Чтобы получить аналогичные результаты можно использовать функции [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST и CONVERT.  
  
```sql  
SELECT ID, CAST(PointValue AS varchar)   
FROM dbo.Points;  
  
SELECT ID, CONVERT(varchar, PointValue)   
FROM dbo.Points;  
```  
  
 Определяемый пользователем тип **Point** предоставляет свои координаты X и Y как свойства, которые затем можно выбрать по отдельности. Следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] выбирает координаты X и Y отдельно:  
  
```sql  
SELECT ID, PointValue.X AS xVal, PointValue.Y AS yVal   
FROM dbo.Points;  
```  
  
 Свойства X и Y возвращают целочисленные значения, которые отображаются в результирующем наборе.  
  
```  
ID xVal yVal  
-- ---- ----  
 1    3    4  
 2    1    5  
 3    1   99  
```  
  
## <a name="working-with-variables"></a>Работа с переменными  
 Можно также работать с переменными с помощью инструкции DECLARE, чтобы присвоить значение переменной определяемому пользователем типу. Следующие операторы присваивают значение с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции SET и отображают результаты, вызывая для переменной метод определяемого пользователем типа ( **ToString** ).  
  
```sql  
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
  
```sql  
DECLARE @PointValue Point;  
SELECT @PointValue = PointValue FROM dbo.Points  
    WHERE ID = 2;  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 Различие между использованием инструкций SELECT и SET для присваиваний значений переменных состоит в том, что SELECT позволяет присваивать значения нескольких переменных в одной инструкции SELECT, в то время как синтаксис SET требует для каждого присваивания переменной отдельной инструкции SET.  
  
## <a name="comparing-data"></a>Сравнение данных  
 Операторы сравнения можно использовать для сравнения значений в определяемом пользователем типе, если для свойства **IsByteOrdered** задано **значение true** при определении класса. Дополнительные сведения см. [в разделе Создание определяемого пользователем типа](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md).  
  
```sql  
SELECT ID, PointValue.ToString() AS Points   
FROM dbo.Points  
WHERE PointValue > CONVERT(Point, '2,2');  
```  
  
 Можно сравнить внутренние значения определяемого пользователем типа независимо от параметра **IsByteOrdered** , если сами значения являются сравнимыми. Следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] выбирает строки, в которых X больше, чем Y:  
  
```sql  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points  
WHERE PointValue.X < PointValue.Y;  
```  
  
 Можно также использовать операторы сравнения с переменными, как показано в данном запросе, который ищет совпадения с PointValue.  
  
```sql  
DECLARE @ComparePoint Point;  
SET @ComparePoint = CONVERT(Point, '3,4');  
SELECT ID, PointValue.ToString() AS MatchingPoint   
FROM dbo.Points  
WHERE PointValue = @ComparePoint;  
```  
  
## <a name="invoking-udt-methods"></a>Вызов методов определяемого пользователем типа  
 Можно также вызывать методы, которые определены в определяемом пользователем типе [!INCLUDE[tsql](../../includes/tsql-md.md)]. Класс **Point** содержит три метода, **Distance**, **дистанцефром**и **дистанцефромкси**. Примеры кода, определяющие эти три метода, см. в разделе [программирование определяемых пользователем типов](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
 Следующая [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкция вызывает метод **PointValue. Distance** :  
  
```sql  
SELECT ID, PointValue.X AS [Point.X],   
    PointValue.Y AS [Point.Y],  
    PointValue.Distance() AS DistanceFromZero   
FROM dbo.Points;  
```  
  
 Результаты отображаются в столбце **расстояние** :  
  
```  
ID X  Y  Distance  
-- -- -- ----------------  
 1  3  4                5  
 2  1  5 5.09901951359278  
 3  1 99 99.0050503762308  
```  
  
 Метод **дистанцефром** принимает аргумент типа данных **Point** и отображает расстояние от указанной точки до PointValue:  
  
```sql  
SELECT ID, PointValue.ToString() AS Pnt,  
   PointValue.DistanceFrom(CONVERT(Point, '1,99')) AS DistanceFromPoint  
FROM dbo.Points;  
```  
  
 Результаты выводятся в результатах метода **дистанцефром** для каждой строки в таблице:  
  
```  
ID Pnt DistanceFromPoint  
-- --- -----------------  
 1 3,4  95.0210502993942  
 2 1,5                94  
 3 1,9                90  
```  
  
 Метод **дистанцефромкси** принимает точки по отдельности в качестве аргументов:  
  
```sql  
SELECT ID, PointValue.X as X, PointValue.Y as Y,   
PointValue.DistanceFromXY(1, 99) AS DistanceFromXY   
FROM dbo.Points  
```  
  
 Результирующий набор совпадает с методом **дистанцефром** .  
  
## <a name="updating-data-in-a-udt-column"></a>Обновление данных в столбце определяемого пользователем типа  
 Чтобы обновлять данные в столбце определяемого пользователем типа, используется инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE. Также можно использовать метод определяемого пользователем типа, чтобы обновить состояние объекта. Следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] обновляет одну строку в таблице:  
  
```sql  
UPDATE dbo.Points  
SET PointValue = CAST('1,88' AS Point)  
WHERE ID = 3  
```  
  
 Также можно обновлять элементы определяемого пользователем типа отдельно. Следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] обновляет только координату Y:  
  
```sql  
UPDATE dbo.Points  
SET PointValue.Y = 99  
WHERE ID = 3  
```  
  
 Если определяемый пользователем тип был определен с порядком байтов, установленным в **значение true**, [!INCLUDE[tsql](../../includes/tsql-md.md)] может оценивать столбец определяемого пользователем типа в предложении WHERE.  
  
```sql  
UPDATE dbo.Points  
SET PointValue = '4,5'  
WHERE PointValue = '3,4';  
```  
  
### <a name="updating-limitations"></a>Ограничения обновлений  
 Нельзя обновить несколько свойств за раз с помощью инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)]. Например, следующая инструкция UPDATE выполняется с ошибкой, так как нельзя использовать одно и то же имя столбца дважды в одной инструкции UDATE.  
  
```sql  
UPDATE dbo.Points  
SET PointValue.X = 5, PointValue.Y = 99  
WHERE ID = 3  
```  
  
 Чтобы обновить каждую точку отдельно, необходимо создать метод мутатора в сборке определяемого пользователем типа Point. Можно затем обратиться к методу мутатора в инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE для обновления объекта, как показано ниже:  
  
```sql  
UPDATE dbo.Points  
SET PointValue.SetXY(5, 99)  
WHERE ID = 3  
```  
  
## <a name="deleting-data-in-a-udt-column"></a>Удаление данных из столбца определяемого пользователем типа  
 Чтобы удалить данные в определяемом пользователем типе, используется инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE. Следующая инструкция удаляет все строки из таблицы, которые удовлетворяют критерию, указанному в предложении WHERE. Если предложение WHERE пропущено в инструкции DELETE, будут удалены все строки таблицы.  
  
```sql  
DELETE FROM dbo.Points  
WHERE PointValue = CAST('1,99' AS Point)  
```  
  
 Инструкция UPDATE используется, если необходимо удалить значения в столбце определяемого пользователем типа и оставить другие значения строки без изменений. Этот пример задает столбцу PointValue значение NULL.  
  
```sql  
UPDATE dbo.Points  
SET PointValue = null  
WHERE ID = 2  
```  
  
## <a name="see-also"></a>См. также  
 [Работа с определяемыми пользователем типами в SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)  
  
  
