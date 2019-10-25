---
title: Обработка значений NULL
description: Демонстрирует работу с GUID и значениями uniqueidentifier в SQL Server и .NET.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 6ae2bc8d816dd2bc32572447483dacd76dd967f0
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452181"
---
# <a name="handling-null-values"></a>Обработка значений NULL

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Значение NULL в реляционной базе данных используется, если значение в столбце неизвестно или отсутствует. NULL не является ни пустой строкой (для типов данных character или DateTime), ни нулевым значением (для числовых типов данных). В спецификации ANSI SQL-92 указано, что значение null должно быть одинаковым для всех типов данных, чтобы все значения NULL обрабатывались единообразно. <xref:System.Data.SqlTypes> пространство имен обеспечивает семантику со значением NULL, реализуя интерфейс <xref:System.Data.SqlTypes.INullable>. Каждый из типов данных в <xref:System.Data.SqlTypes> имеет собственное свойство `IsNull` и `Null` значение, которое может быть назначено экземпляру этого типа данных.  
  
> [!NOTE]
>  В .NET Framework версии 2,0 и .NET Core версии 1,0 появилась поддержка типов, допускающих значение null, что позволяет программистам расширять тип значения для представления всех значений базового типа. Эти типы CLR, допускающие значение null, представляют экземпляр структуры <xref:System.Nullable>. Эта возможность особенно полезна, если типы значений упакованы и распакованы, что обеспечивает улучшенную совместимость с типами объектов. Типы CLR, допускающие значение null, не предназначены для хранения значений NULL базы данных, так как ANSI SQL NULL не работает так же, как ссылка на `null` (или `Nothing` в Visual Basic). Для работы со значениями NULL SQL для базы данных используйте <xref:System.Data.SqlTypes> значения NULL вместо <xref:System.Nullable>. Дополнительные сведения о работе с типами данных CLR, допускающими значение null, см. C# в C# разделе Типы, [допускающие](https://docs.microsoft.com/dotnet/csharp/programming-guide/nullable-types/using-nullable-types/) [значения NULL](https://docs.microsoft.com/dotnet/csharp/programming-guide/nullable-types/), а для см.  
  
## <a name="nulls-and-three-valued-logic"></a>Значения NULL и логика с тремя значениями  
Разрешение значений NULL в определениях столбцов вводит в приложение логику с тремя значениями. Результатом сравнения может быть одно из трех условий:  
  
- True  
  
- False  
  
- Неизвестно  
  
Поскольку значение NULL считается неизвестным, два значения NULL, сравниваемые друг с другом, не считаются равными. В выражениях, использующих арифметические операторы, если какой-либо из операндов имеет значение null, результат также равен null.  
  
## <a name="nulls-and-sqlboolean"></a>Значения NULL и SqlBoolean  
Сравнение любого <xref:System.Data.SqlTypes> будет возвращать <xref:System.Data.SqlTypes.SqlBoolean>. Функция `IsNull` для каждой `SqlType` возвращает <xref:System.Data.SqlTypes.SqlBoolean> и может использоваться для проверки значений NULL. В следующих таблицах истин показано, как операторы AND, OR и NOT в наличии значения NULL. (T = true, F = false и U = Unknown или null.)  
  
![Таблица истинности](../media/truthtable-bpuedev11.gif "|::ref1::|")  
  
### <a name="understanding-the-ansi_nulls-option"></a>Основные сведения о параметре ANSI_NULLS  
<xref:System.Data.SqlTypes> предоставляет ту же семантику, что и, если параметр ANSI_NULLS установлен в SQL Server. Все арифметические операторы (+, -, *, /, %), битовые операции (~, &, &#124;) и большинство функций возвращают NULL, если какие-либо из операндов или аргументов равны NULL, за исключением операндов или аргументов для свойства `IsNull`.  
  
Стандарт ANSI SQL-92 не поддерживает *columnName* = NULL в предложении WHERE. В SQL Server параметр ANSI_NULLS управляет допустимостью значений NULL по умолчанию в базе данных и вычислением сравнений со значениями NULL. Если параметр ANSI_NULLS включен (по умолчанию), то при проверке значений NULL в выражениях должен использоваться оператор IS NULL. Например, результатом следующего сравнения всегда является неизвестность при включенном параметре ANSI_NULLS:  
  
```console
colname > NULL  
```  
  
Сравнение с переменной, содержащей значение null, также приводит к неизвестному результату:  
  
```console
colname > @MyVariable  
```  
  
Для тестирования на значение NULL используются предикаты IS NULL и IS NOT NULL. Это может усложнить предложение WHERE. Например, столбец Территорид в таблице AdventureWorks Customer допускает значения NULL. Если инструкция SELECT используется для тестирования на значения NULL в дополнение к другим, она должна включать предикат IS NULL:  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
Если в SQL Server установлен параметр ANSI_NULLS OFF, можно создать выражения, которые используют оператор равенства для сравнения со значением NULL. Однако нельзя запретить другим соединениям задавать параметры null для этого соединения. Использование параметра имеет значение NULL для проверки того, что значения NULL всегда работают, независимо от настроек ANSI_NULLS для соединения.  
  
Установка параметра ANSI_NULLS OFF не поддерживается в `DataSet`, которая всегда соответствует стандарту ANSI SQL-92 для обработки значений NULL в <xref:System.Data.SqlTypes>.  
  
## <a name="assigning-null-values"></a>Присвоение значений NULL  
Значения NULL являются специальными, и их семантика хранения и назначения различается в разных системах типов и системах хранения. `Dataset` предназначен для использования с различными системами типов и хранения.  
  
В этом разделе описывается семантика NULL для присвоения значений NULL <xref:System.Data.DataColumn> в <xref:System.Data.DataRow> в различных системах типов.  
  
`DBNull.Value`  
Это назначение допустимо для `DataColumn` любого типа. Если тип реализует `INullable`, `DBNull.Value` приводится к соответствующему строго типизированному значению NULL.  
  
`SqlType.Null`  
Все типы данных <xref:System.Data.SqlTypes> реализуют `INullable`. Если строго типизированное значение NULL может быть преобразовано в тип данных столбца с помощью операторов неявного приведения, назначение должно проходить через. В противном случае выдается недопустимое исключение приведения.  
  
`null`  
Если значение null является допустимым для данного `DataColumn` типа данных, оно приводится к соответствующему `DbNull.Value` или `Null`, связанному с типом `INullable` (`SqlType.Null`).  
  
`derivedUdt.Null`  
Для столбцов определяемых пользователем типов значения NULL всегда хранятся в зависимости от типа, связанного с `DataColumn`. Рассмотрим случай определяемого пользователем типа, связанного с `DataColumn`, который не реализует `INullable` во время выполнения вложенного класса. В этом случае, если строго типизированное значение null, связанное с производным классом, назначено, оно сохраняется как нетипизированный `DbNull.Value`, так как хранилище NULL всегда согласуется с типом данных DataColumn.  
  
> [!NOTE]
>  Структура `Nullable<T>` или <xref:System.Nullable> в настоящее время не поддерживается в `DataSet`.  
  
### <a name="multiple-column-row-assignment"></a>Присваивание нескольких столбцов (строк)  
`DataTable.Add`, `DataTable.LoadDataRow` или другие API-интерфейсы, принимающие <xref:System.Data.DataRow.ItemArray%2A>, которые сопоставляются со строкой, сопоставляют значение NULL со значением по умолчанию DataColumn. Если объект в массиве содержит `DbNull.Value` или его строго типизированный аналог, применяются те же правила, которые описаны выше.  
  
Кроме того, следующие правила применяются к экземпляру `DataRow.["columnName"]` назначений NULL:  
  
- Используемое по умолчанию значение *default* является `DbNull.Value` для всех столбцов, за исключением строго типизированных нулевых столбцов с допустимыми строго типизированными значениями NULL.  
  
- Значения NULL никогда не записываются во время сериализации в XML-файлы (как в xsi: nil).  
  
- Все значения, отличные от NULL, включая параметры по умолчанию, всегда записываются при сериализации в XML. Это отличается от семантики XSD/XML, где значение null (xsi: nil) является явным и значение по умолчанию является неявным (если отсутствует в XML, проверяющий синтаксический анализатор может получить его из связанной схемы XSD). Противоположное справедливо для `DataTable`: значение null является неявным, а значение по умолчанию — Explicit.  
  
- Всем отсутствующим значениям столбцов для строк, считываемых из входных данных XML, присваивается значение NULL. Строкам, созданным с помощью <xref:System.Data.DataTable.NewRow%2A> или аналогичным методам, присваивается значение по умолчанию DataColumn.  
  
- Метод <xref:System.Data.DataRow.IsNull%2A> возвращает `true` как для `DbNull.Value`, так и для `INullable.Null`.  
  
## <a name="assigning-null-values"></a>Присвоение значений NULL  
Значением по умолчанию для любого экземпляра <xref:System.Data.SqlTypes> является null.  
  
Значения NULL в <xref:System.Data.SqlTypes> относятся к типу и не могут быть представлены одним значением, например `DbNull`. Чтобы проверить значения NULL, используйте свойство `IsNull`.  
  
Значения NULL могут быть назначены <xref:System.Data.DataColumn>, как показано в следующем примере кода. Можно напрямую назначить значения NULL для `SqlTypes` переменных без запуска исключения.  
  
### <a name="example"></a>Пример  
В следующем примере кода создается <xref:System.Data.DataTable> с двумя столбцами, определенными как <xref:System.Data.SqlTypes.SqlInt32> и <xref:System.Data.SqlTypes.SqlString>. Код добавляет одну строку известных значений, одну строку значений NULL, а затем выполняет итерацию по <xref:System.Data.DataTable>, присваивая значения переменным и отображая выходные данные в окне консоли.  
  
[!code-csharp[DataWorks SqlInt32_IsNull#1](~/../sqlclient/doc/samples/SqlInt32_IsNull.cs#1)]
  
В этом примере отображаются следующие результаты.  
  
```console
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Сравнение значений NULL с SqlTypes и типами CLR  
При сравнении значений NULL важно понимать разницу между тем, как метод `Equals` вычисляет значения NULL в <xref:System.Data.SqlTypes> в сравнении с тем, как оно работает с типами CLR. Все методы <xref:System.Data.SqlTypes> `Equals` используют семантику базы данных для вычисления значений NULL: Если одно или оба значения равны NULL, то сравнение дает значение null. С другой стороны, при использовании метода `Equals` CLR для двух <xref:System.Data.SqlTypes> будет возвращать значение true, если оба значения равны NULL. Это отражает разницу между использованием метода экземпляра, такого как метод `String.Equals` CLR, и использованием статического/общего метода `SqlString.Equals`.  
  
В следующем примере показана разница между методами `SqlString.Equals` и `String.Equals`, когда каждый передается пара значений NULL, а затем пара пустых строк.  
  
[!code-csharp[DataWorks SqlString_Equals#1](~/../sqlclient/doc/samples/SqlString_Equals.cs#1)]
  
Получается следующий вывод:  
  
```console
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True   
```  
  
## <a name="next-steps"></a>Следующие шаги
- [Типы данных SQL Server и ADO.NET](sql-server-data-types.md)
