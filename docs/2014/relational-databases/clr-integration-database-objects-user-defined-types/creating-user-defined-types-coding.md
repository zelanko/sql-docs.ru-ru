---
title: Определяемые пользователем типы кодирования | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- validation [CLR integration]
- UDTs [CLR integration], coding
- UserDefined serialization format [CLR integration]
- Point UDT
- Parse method
- null values [CLR integration]
- ToString method
- ValidatePoint method
- attributes [CLR integration]
- coding user-defined types [CLR integration]
- Read method
- Write method
- nullability [CLR integration]
- user-defined types [CLR integration], coding
- Currency UDT
- validating UDT values
- exposing UDT properties [CLR integration]
ms.assetid: 1e5b43b3-4971-45ee-a591-3f535e2ac722
caps.latest.revision: 36
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 25560f82b1a697618dd606f7df8393abb74727c6
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37354426"
---
# <a name="coding-user-defined-types"></a>Разработка кода для определяемых пользователем типов
  При разработке определяемого пользователем типа необходимо реализовать различные функциональные возможности в зависимости от того, реализуется ли определяемый пользователем тип в виде класса или структуры, а также от выбранных параметров формата и сериализации.  
  
 Пример, приведенный в этом разделе, иллюстрирует реализацию определяемого пользователем типа `Point` в виде `struct` (или на языке Visual Basic — `Structure`). Определяемый пользователем тип `Point` содержит координаты X и Y, реализованные как процедуры свойств.  
  
 При определении пользовательского типа необходимы следующие пространства имен:  
  
```vb  
Imports System  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
```  
  
```csharp  
using System;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
```  
  
 Пространство имен `Microsoft.SqlServer.Server` содержит объекты, необходимые для реализации различных атрибутов определяемого пользователем типа, а пространство имен `System.Data.SqlTypes` содержит классы, представляющие собственные типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], доступные для сборки. Разумеется, конкретной сборке для правильной работы могут понадобиться и другие пространства имен. Определяемый пользователем тип `Point` использует также пространство имен `System.Text` для работы со строками.  
  
> [!NOTE]  
>  Выполнение объектов базы данных Visual C++, например UDT, скомпилированных с помощью параметра `/clr:pure`, не поддерживается.  
  
## <a name="specifying-attributes"></a>Определение атрибутов  
 Атрибуты определяют, каким образом сериализация используется для создания хранимых представлений определяемых пользователем типов, а также для передачи таких типов клиенту по значению.  
  
 Атрибут `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` является обязательным. Атрибут `Serializable` является необязательным. Также можно указать атрибут `Microsoft.SqlServer.Server.SqlFacetAttribute` для задания информации о возвращаемом типе, определяемом пользователем. Дополнительные сведения см. в статье [Пользовательские атрибуты процедур CLR](../clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md).  
  
### <a name="point-udt-attributes"></a>Атрибуты определяемого пользователем типа Point  
 Метод `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` задает для определяемого пользователем типа `Point` формат хранения `Native`. Свойству `IsByteOrdered` присваивается значение `true`, а это гарантирует, что результаты сравнения в SQL Server будут такими же, как если бы сравнение проводилось в управляемом коде. Определяемый пользователем тип реализует интерфейс `System.Data.SqlTypes.INullable`, чтобы определяемый пользователем тип мог работать со значениями NULL.  
  
 В следующем фрагменте кода показаны атрибуты определяемого пользователем типа `Point`.  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True)> _  
  Public Structure Point  
    Implements INullable  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true)]  
public struct Point : INullable  
{  
```  
  
## <a name="implementing-nullability"></a>Реализация допустимости значений NULL  
 Помимо задания необходимых атрибутов для сборок определяемый пользователем тип должен также поддерживать допустимость значений NULL. Определяемые пользователем типы, загружаемые в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], позволяют работать со значениями NULL, но условием того, чтобы определяемый пользователем тип распознавал значение NULL, является реализация интерфейса `System.Data.SqlTypes.INullable`.  
  
 Следует создать свойство с именем `IsNull`, необходимое для распознавания значений NULL из кода CLR. При обнаружении в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра определяемого пользователем типа со значением NULL происходит его сохранение с использованием обычных методов работы со значениями NULL. Сервер не теряет времени на сериализацию и десериализацию определяемого пользователем типа, обнаруживая, что это не требуется, а также не расходует место для хранения определяемого пользователем типа со значением NULL. Проверка на наличие значений NULL проводится каждый раз, когда значение определяемого пользователем типа передается из среды CLR, а это означает, что конструкция языка [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL для проверки определяемых пользователем типов на значения NULL всегда должна работать. Свойство `IsNull` используется также сервером для проверки равенства экземпляра значению NULL. Если сервер определил, что определяемый пользователем тип равен NULL, то может использовать собственные методы работы со значениями NULL.  
  
 Метод `get()` свойства `IsNull` не рассчитан на возникновение каких-либо особых случаев. Если переменная типа `Point` `@p` равна `Null`, то выражение `@p.IsNull` по определению равно «NULL», а не «1». Это объясняется тем, что атрибут `SqlMethod(OnNullCall)` метода `IsNull get()` по умолчанию имеет значение «false». Таким образом, объект равен `Null`, поэтому при запросе этого свойства объект не десериализуется, метод не вызывается и происходит возврат значения по умолчанию «NULL».  
  
### <a name="example"></a>Пример  
 В следующем примере переменная `is_Null` является закрытой и хранит состояние NULL экземпляра определяемого пользователем типа. В программном коде должно поддерживаться соответствующее значение переменной `is_Null`. Определяемый пользователем тип должен также иметь статическое свойство с именем `Null`, возвращающее экземпляр определяемого пользователем типа со значением (равным NULL). Это позволяет возвращать значение NULL в определяемом пользователем типе, если экземпляр в базе данных действительно равен NULL.  
  
```vb  
Private is_Null As Boolean  
  
Public ReadOnly Property IsNull() As Boolean _  
   Implements INullable.IsNull  
    Get  
        Return (is_Null)  
    End Get  
End Property  
  
Public Shared ReadOnly Property Null() As Point  
    Get  
        Dim pt As New Point  
        pt.is_Null = True  
        Return (pt)  
    End Get  
End Property  
```  
  
```csharp  
private bool is_Null;  
  
public bool IsNull  
{  
    get  
    {  
        return (is_Null);  
    }  
}  
  
public static Point Null  
{  
    get  
    {  
        Point pt = new Point();  
        pt.is_Null = true;  
        return pt;  
    }  
}  
```  
  
### <a name="is-null-vs-isnull"></a>Сравнение IS NULL и IsNull  
 Рассмотрим таблицу, содержащую схему Points(id int, location Point), где тип `Point` представляет собой определяемый пользователем тип среды CLR, и следующие запросы:  
  
```  
--Query 1  
SELECT ID  
FROM Points  
WHERE NOT (location IS NULL) -- Or, WHERE location IS NOT NULL;  
```  
  
```  
--Query 2:  
SELECT ID  
FROM Points  
WHERE location.IsNull = 0;  
```  
  
 Оба запроса возвращают идентификаторы точек, местонахождение которых отлично от `Null`. В запросе 1 используется нормальная обработка значений NULL, а десериализация определяемых пользователем типов не требуется. С другой стороны, в запросе 2 приходится обеспечивать десериализацию каждого объекта, отличного от `Null`, и вызывать среду CLR для получения значения свойства `IsNull`. Очевидно, что использование `IS NULL` позволяет достичь более высокой производительности, поэтому нет никакого смысла прибегать к чтению значения свойства `IsNull` определяемого пользователем типа из кода [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Так для чего же используется свойство `IsNull`? Во-первых, для определения того, получено ли значение `Null` из кода CLR. Во-вторых, серверу требуется способ проверки того, имеет ли экземпляр значение `Null`, поэтому это свойство также используется сервером. После определения, что экземпляр действительно равен `Null`, сервер может использовать собственные методы работы со значениями NULL.  
  
## <a name="implementing-the-parse-method"></a>Реализация синтаксического анализа  
 Методы `Parse` и `ToString` осуществляют прямые и обратные преобразования определяемых пользователем типов в строки. Метод `Parse` позволяет преобразовывать строку в определяемый пользователем тип. Он должен быть объявлен как `static` (или `Shared` в Visual Basic) и принимать параметр типа `System.Data.SqlTypes.SqlString`.  
  
 В данном примере реализован метод `Parse` для определяемого пользователем типа `Point`, который выделяет координаты X и Y. Метод `Parse` имеет единственный аргумент типа `System.Data.SqlTypes.SqlString`, причем предполагается, что величины X и Y передаются в виде строки, разделенной запятыми. Присваивание атрибуту `Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall` значения `false` гарантирует, что метод `Parse` не может быть вызван из экземпляра Point (равного NULL).  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
    return pt;  
}  
```  
  
## <a name="implementing-the-tostring-method"></a>Реализация метода ToString  
 Метод `ToString` преобразует значение определяемого пользователем типа `Point` в строку. В данном случае для экземпляра `Point`, равного NULL, будет возвращено строковое значение «NULL». Метод `ToString` является обратным по отношению к методу `Parse`, поскольку в нем используется класс `System.Text.StringBuilder` для возврата разделенной запятыми строки типа `System.String`, содержащей значения координат X и Y. Так как **InvokeIfReceiverIsNull** по умолчанию — false, проверка неопределенный экземпляр `Point` не требуется.  
  
```vb  
Private _x As Int32  
Private _y As Int32  
  
Public Overrides Function ToString() As String  
    If Me.IsNull Then  
        Return "NULL"  
    Else  
        Dim builder As StringBuilder = New StringBuilder  
        builder.Append(_x)  
        builder.Append(",")  
        builder.Append(_y)  
        Return builder.ToString  
    End If  
End Function  
```  
  
```csharp  
private Int32 _x;  
private Int32 _y;  
  
public override string ToString()  
{  
    if (this.IsNull)  
        return "NULL";  
    else  
    {  
        StringBuilder builder = new StringBuilder();  
        builder.Append(_x);  
        builder.Append(",");  
        builder.Append(_y);  
        return builder.ToString();  
    }  
}  
```  
  
## <a name="exposing-udt-properties"></a>Предоставление доступа к свойствам определяемого пользователем типа  
 Определяемый пользователем тип `Point` предоставляет доступ к координатам X и Y, реализованным как процедуры свойств для чтения и записи, относящиеся к типу `System.Int32`.  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _x = Value  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _y = Value  
    End Set  
End Property  
```  
  
```csharp  
public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    set   
    {  
        _x = value;  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        _y = value;  
    }  
}  
```  
  
## <a name="validating-udt-values"></a>Проверка значений определяемого пользователем типа  
 При работе с определяемым пользователем типом компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] автоматически преобразовывает двоичные значения в значения определяемого пользователем типа. Этот процесс преобразования включает в себя проверку соответствия значений формату сериализации и проверку того, что значения могут быть десериализованы правильно. Это гарантирует, что значение может быть преобразовано обратно в двоичную форму. В случае определяемого пользователем типа с заданным порядком байтов это также гарантирует, что результирующее двоичное значение совпадет с исходным. Благодаря этому предотвращается сохранение недопустимых значений в базе данных. В некоторых случаях такой уровень проверки недостаточен. Если значения определяемого пользователем типа должны находиться в определенной области или диапазоне, то может потребоваться дополнительная проверка. Например, для определяемого пользователем типа, реализующего дату, может потребоваться, чтобы день был положительным числом, попадающим в определенный диапазон допустимых значений.  
  
 Свойство `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName` класса `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` позволяет задавать имя метода проверки, запускаемого сервером, когда значение присваивается определяемому пользователем типу или преобразуется в определяемый пользователем тип. Свойство `ValidationMethodName` вызывается также при запуске программы bcp, инструкций BULK INSERT, DBCC CHECKDB, DBCC CHECKFILEGROUP, DBCC CHECKTABLE, распределенного запроса и операций удаленных вызовов процедур (RPC) для потоков табличных данных (TDS). Значение по умолчанию для метода `ValidationMethodName` равно NULL. Это означает, что метод проверки не задан.  
  
### <a name="example"></a>Пример  
 В следующем фрагменте кода для класса `Point` показана декларация, которая задает свойство `ValidationMethodName` метода `ValidatePoint`.  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True, _  
  ValidationMethodName:="ValidatePoint")> _  
  Public Structure Point  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true,   
  ValidationMethodName = "ValidatePoint")]  
public struct Point : INullable  
{  
```  
  
 Если метод проверки задан, то должен иметь подпись, которая выглядит, как показано в следующем фрагменте кода:  
  
```vb  
Private Function ValidationFunction() As Boolean  
    If (validation logic here) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidationFunction()  
{  
    if (validation logic here)  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
 Метод проверки может иметь любую область действия, возвращая `true`, если значение допустимо, и `false` — в противном случае. Если метод возвращает `false` или создает исключение, считается, что значение недопустимо, и выдается соответствующее сообщение об ошибке.  
  
 В приведенном примере кода для координат X и Y разрешаются только нулевые и положительные значения.  
  
```vb  
Private Function ValidatePoint() As Boolean  
    If (_x >= 0) And (_y >= 0) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidatePoint()  
{  
    if ((_x >= 0) && (_y >= 0))  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
### <a name="validation-method-limitations"></a>Ограничения метода проверки  
 Сервер вызывает метод проверки при проведении преобразований, а не в тот момент, когда данные вставляются с помощью задания отдельных свойств или с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT.  
  
 Необходимо явно вызывать метод проверки из методов задания свойств и `Parse` метод, если требуется, чтобы метод проверки, чтобы во всех ситуациях. Это не является требованием и в некоторых случаях даже нежелательно.  
  
### <a name="parse-validation-example"></a>Пример проверки при синтаксическом анализе  
 Чтобы убедиться, что `ValidatePoint` метод вызывается в `Point` класса, необходимо вызвать его из `Parse` метод и значения из свойства координат процедур, которые задают X и Y. В следующем фрагменте кода показан способ вызова `ValidatePoint` метод проверки `Parse` функции.  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
  
    ' Call ValidatePoint to enforce validation  
    ' for string conversions.  
    If Not pt.ValidatePoint() Then  
        Throw New ArgumentException("Invalid XY coordinate values.")  
    End If  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
  
    // Call ValidatePoint to enforce validation  
    // for string conversions.  
    if (!pt.ValidatePoint())   
        throw new ArgumentException("Invalid XY coordinate values.");  
    return pt;  
}  
```  
  
### <a name="property-validation-example"></a>Пример проверки при операциях над свойствами  
 В следующем фрагменте кода показан способ вызова `ValidatePoint` метод проверки из процедур свойств, заданных координат X и Y.  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _x  
        _x = Value  
        If Not ValidatePoint() Then  
            _x = temp  
            Throw New ArgumentException("Invalid X coordinate value.")  
        End If  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _y  
        _y = Value  
        If Not ValidatePoint() Then  
            _y = temp  
            Throw New ArgumentException("Invalid Y coordinate value.")  
        End If  
    End Set  
End Property  
```  
  
```csharp  
    public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    // Call ValidatePoint to ensure valid range of Point values.  
    set   
    {  
        Int32 temp = _x;  
        _x = value;  
        if (!ValidatePoint())  
        {  
            _x = temp;  
            throw new ArgumentException("Invalid X coordinate value.");  
        }  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        Int32 temp = _y;  
        _y = value;  
        if (!ValidatePoint())  
        {  
            _y = temp;  
            throw new ArgumentException("Invalid Y coordinate value.");  
        }  
    }  
}  
```  
  
## <a name="coding-udt-methods"></a>Реализация методов определяемого пользователем типа  
 При реализации методов определяемого пользователем типа следует учитывать возможность изменения алгоритма в будущем. Если такая возможность имеется, то следует создать отдельный класс для методов, используемых определяемым пользователем типом. Если алгоритм изменится, можно будет перекомпилировать класс с новым кодом и загрузить сборку в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], не затрагивая определяемый пользователем тип. Во многих случаях определяемые пользователем типы можно загружать заново с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY, но это может вызвать проблемы с существующими данными. Например `Currency` определяемого пользователем ТИПА в состав **AdventureWorks** примере используется база данных **ConvertCurrency** функции для преобразования значений, которая реализована в отдельном классе. Возможно, что в будущем алгоритмы преобразования изменятся непредсказуемым образом или потребуются новые функциональные возможности. Отделение **ConvertCurrency** функции из `Currency` реализации определяемого пользователем ТИПА обеспечивает большую гибкость при планировании для будущих изменений.  
  
### <a name="example"></a>Пример  
 `Point` Класс содержит три простых метода вычисления расстояния: **расстояние**, **DistanceFrom** и **DistanceFromXY**. Каждый из методов возвращает значение `double`, равное расстоянию от `Point` до начала координат, от указанной точки до объекта `Point` и от заданных координат X и Y до объекта `Point`. **Расстояние** и **DistanceFrom** каждый вызов **DistanceFromXY**и демонстрируется использование различных аргументов для каждого метода.  
  
```vb  
' Distance from 0 to Point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function Distance() As Double  
    Return DistanceFromXY(0, 0)  
End Function  
  
' Distance from Point to the specified point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFrom(ByVal pFrom As Point) As Double  
    Return DistanceFromXY(pFrom.X, pFrom.Y)  
End Function  
  
' Distance from Point to the specified x and y values.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFromXY(ByVal ix As Int32, ByVal iy As Int32) _  
    As Double  
    Return Math.Sqrt(Math.Pow(ix - _x, 2.0) + Math.Pow(iy - _y, 2.0))  
End Function  
```  
  
```csharp  
// Distance from 0 to Point.  
[SqlMethod(OnNullCall = false)]  
public Double Distance()  
{  
    return DistanceFromXY(0, 0);  
}  
  
// Distance from Point to the specified point.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFrom(Point pFrom)  
{  
    return DistanceFromXY(pFrom.X, pFrom.Y);  
}  
  
// Distance from Point to the specified x and y values.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFromXY(Int32 iX, Int32 iY)  
{  
    return Math.Sqrt(Math.Pow(iX - _x, 2.0) + Math.Pow(iY - _y, 2.0));  
}  
```  
  
### <a name="using-sqlmethod-attributes"></a>Использование атрибутов SqlMethod  
 Класс `Microsoft.SqlServer.Server.SqlMethodAttribute` предоставляет настраиваемые атрибуты, которые можно использовать в определениях метода, чтобы пометить метод как детерминированный, задать поведение при вызове на экземпляре (равном NULL) или указать, что метод является мутатором. Предполагается, что эти свойства имеют определенные значения по умолчанию, а настраиваемый атрибут используется только тогда, когда необходимо задать другое значение.  
  
> [!NOTE]  
>  Класс `SqlMethodAttribute` наследуется от `SqlFunctionAttribute`, поэтому класс `SqlMethodAttribute` наследует поля `FillRowMethodName` и `TableDefinition` от класса `SqlFunctionAttribute`. Это подразумевает, что существует возможность написать возвращающий табличное значение метод, который не является вариантом. Метод компилируется, и сборка развертывается, но ошибка о `IEnumerable` возвращают тип возникает во время выполнения со следующим сообщением: «метод, свойство или поле "\<имя >" в классе\<класс > "в сборке"\<сборки > "имеет недопустимый возвращаемый тип.»  
  
 В следующей таблице рассматриваются некоторые важные свойства класса `Microsoft.SqlServer.Server.SqlMethodAttribute`, которые можно использовать для методов определяемого пользователем типа, и перечисляются их значения по умолчанию.  
  
 DataAccess  
 Указывает, что функция производит доступ к пользовательским данным, хранимым в локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Значение по умолчанию — `DataAccessKind``None`.  
  
 IsDeterministic  
 Указывает, производит ли функция одни и те же выходные значения при одинаковых наборах входных значений и одинаковых состояниях базы данных. Значение по умолчанию — `false`.  
  
 IsMutator  
 Указывает, вызывает ли метод изменение состояния экземпляра определяемого пользователем типа. Значение по умолчанию — `false`.  
  
 IsPrecise  
 Указывает, содержит ли функция вычисления с потерей точности (например, операции с плавающей запятой). Значение по умолчанию — `false`.  
  
 OnNullCall  
 Указывает, вызывается ли метод, если в качестве ссылки на входные аргументы заданы значения NULL. Значение по умолчанию — `true`.  
  
### <a name="example"></a>Пример  
 Свойство `Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator` позволяет указать, что метод производит изменение состояния экземпляра определяемого пользователем типа. Язык [!INCLUDE[tsql](../../includes/tsql-md.md)] не позволяет задать два свойства определяемого пользователем типа в предложении SET одной инструкции UPDATE. Однако можно создать метод-мутатор, изменяющий два члена определяемого пользователем типа сразу.  
  
> [!NOTE]  
>  Методы-мутаторы в запросах не допускаются. Их можно вызывать только в инструкциях присваивания или изменения данных. Если метод, помеченный как мутатор, не возвращает `void` (или в языке Visual Basic не представляет собой `Sub`), то выполнение инструкции CREATE TYPE завершится с ошибкой.  
  
 Следующая инструкция подразумевает наличие определяемого пользователем типа `Triangles`, имеющего метод `Rotate`. В следующей инструкции изменения данных языка [!INCLUDE[tsql](../../includes/tsql-md.md)] вызывается метод `Rotate`:  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 Метод `Rotate` обозначается атрибутом `SqlMethod` со свойством `IsMutator` (равным `true`), так что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может пометить этот метод как мутатор. Кроме того, в данном коде для атрибута `OnNullCall` задается значение `false`, а это служит для сервера указанием, что метод возвращает ссылку, равную NULL (в языке Visual Basic — `Nothing`), если любой из входных параметров представляет собой ссылку, равную NULL.  
  
```vb  
<SqlMethod(IsMutator:=True, OnNullCall:=False)> _  
Public Sub Rotate(ByVal anglex as Double, _  
  ByVal angley as Double, ByVal anglez As Double)   
   RotateX(anglex)  
   RotateY(angley)  
   RotateZ(anglez)  
End Sub  
```  
  
```csharp  
[SqlMethod(IsMutator = true, OnNullCall = false)]  
public void Rotate(double anglex, double angley, double anglez)   
{  
   RotateX(anglex);  
   RotateY(angley);  
   RotateZ(anglez);  
}  
```  
  
## <a name="implementing-a-udt-with-a-user-defined-format"></a>Реализация определяемого пользователем типа в определяемом пользователем формате  
 При реализации определяемого пользователем типа в определяемом пользователем формате необходимо реализовать методы `Read` и `Write`, реализующие интерфейс Microsoft.SqlServer.Server.IBinarySerialize для сериализации и десериализации данных определяемого пользователем типа. Необходимо также задать свойство `MaxByteSize` класса `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`.  
  
### <a name="the-currency-udt"></a>Определяемый пользователем тип Currency  
 Определяемый пользователем тип `Currency` входит в число образцов CLR, которые можно установить вместе с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]).  
  
 Определяемый пользователем тип `Currency` поддерживает обработку денежных сумм в денежной системе конкретной культуры. Должны быть определены два поля: значение типа `string` для поля `CultureInfo`, задающее источник определения валюты (например, en-us), и значение типа `decimal` для поля `CurrencyValue`, представляющего денежные суммы.  
  
 Определяемый пользователем тип `Currency` реализует интерфейс `System.IComparable`, предоставляющий единственный метод `System.IComparable.CompareTo`, хотя сервер не использует этот метод для операций сравнения. Он используется на клиенте в ситуациях, когда необходимо провести точное сравнение или сортировку значений денежных сумм внутри культур.  
  
 Код, работающий в среде CLR, сравнивает культуры отдельно от значений суммы. Для кода на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] сравнение определяется следующими действиями.  
  
1.  Для атрибута `IsByteOrdered` задается значение true, а это служит для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] указанием, что для сравнения необходимо использовать сохраненные на диске двоичные представления.  
  
2.  С помощью метода `Write` определяемого пользователем типа `Currency` определяется, как сохраняется значение данного типа на диске и, следовательно, как проводятся сравнение и сортировка данного типа в операциях языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
3.  Значения определяемого пользователем типа `Currency` нужно сохранять в следующем двоичном формате.  
  
    1.  Культура сохраняется в виде строки в кодировке UTF-16 для байтов 0-19 с дополнением нулевыми символами справа.  
  
    2.  Байты с 20 и выше используются для сохранения десятичного значения денежной суммы.  
  
 Дополнение нужно для того, чтобы гарантировать полное отделение значения культуры от значения суммы. Тогда при сравнении одного значения определяемого пользователем типа с другим в коде [!INCLUDE[tsql](../../includes/tsql-md.md)] значение одной культуры можно будет побайтно сравнить со значением другой культуры, а значения байтов одной денежной суммы — со значениями байтов другой денежной суммы.  
  
 Для получения полного кода для `Currency` определяемого пользователем ТИПА, выполните инструкции по установке CLR образцов в [образцы SQL Server Database Engine](http://msftengprodsamples.codeplex.com/).  
  
### <a name="currency-attributes"></a>Атрибуты Currency  
 Определяемый пользователем тип `Currency` содержит следующие атрибуты.  
  
```vb  
<Serializable(), Microsoft.SqlServer.Server.SqlUserDefinedType( _  
    Microsoft.SqlServer.Server.Format.UserDefined, _  
    IsByteOrdered:=True, MaxByteSize:=32), _  
    CLSCompliant(False)> _  
Public Structure Currency  
Implements INullable, IComparable, _  
Microsoft.SqlServer.Server.IBinarySerialize  
```  
  
```csharp  
[Serializable]  
[SqlUserDefinedType(Format.UserDefined,   
    IsByteOrdered = true, MaxByteSize = 32)]  
    [CLSCompliant(false)]  
    public struct Currency : INullable, IComparable, IBinarySerialize  
    {  
```  
  
## <a name="creating-read-and-write-methods-with-ibinaryserialize"></a>Создание методов чтения и записи с помощью интерфейса IBinarySerialize  
 При выборе формата сериализации `UserDefined` необходимо также реализовать интерфейс `IBinarySerialize` и создать собственные методы `Read` и `Write`. Следующие процедуры определяемого пользователем типа `Currency` используют классы `System.IO.BinaryReader` и `System.IO.BinaryWriter` для чтения данных из определяемого пользователем типа и записи в него.  
  
```vb  
' IBinarySerialize methods  
' The binary layout is as follow:  
'    Bytes 0 - 19: Culture name, padded to the right with null  
'    characters, UTF-16 encoded  
'    Bytes 20+: Decimal value of money  
' If the culture name is empty, the currency is null.  
Public Sub Write(ByVal w As System.IO.BinaryWriter) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Write  
    If Me.IsNull Then  
        w.Write(nullMarker)  
        w.Write(System.Convert.ToDecimal(0))  
        Return  
    End If  
  
    If cultureName.Length > cultureNameMaxSize Then  
        Throw New ApplicationException(String.Format(CultureInfo.CurrentUICulture, _  
           "{0} is an invalid culture name for currency as it is too long.", cultureNameMaxSize))  
    End If  
  
    Dim paddedName As String = cultureName.PadRight(cultureNameMaxSize, CChar(vbNullChar))  
  
    For i As Integer = 0 To cultureNameMaxSize - 1  
        w.Write(paddedName(i))  
    Next i  
  
    ' Normalize decimal value to two places  
    currencyVal = Decimal.Floor(currencyVal * 100) / 100  
    w.Write(currencyVal)  
End Sub  
  
Public Sub Read(ByVal r As System.IO.BinaryReader) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Read  
    Dim name As Char() = r.ReadChars(cultureNameMaxSize)  
    Dim stringEnd As Integer = Array.IndexOf(name, CChar(vbNullChar))  
  
    If stringEnd = 0 Then  
        cultureName = Nothing  
        Return  
    End If  
  
    cultureName = New String(name, 0, stringEnd)  
    currencyVal = r.ReadDecimal()  
End Sub  
  
```  
  
```csharp  
// IBinarySerialize methods  
// The binary layout is as follow:  
//    Bytes 0 - 19:Culture name, padded to the right   
//    with null characters, UTF-16 encoded  
//    Bytes 20+:Decimal value of money  
// If the culture name is empty, the currency is null.  
public void Write(System.IO.BinaryWriter w)  
{  
    if (this.IsNull)  
    {  
        w.Write(nullMarker);  
        w.Write((decimal)0);  
        return;  
    }  
  
    if (cultureName.Length > cultureNameMaxSize)  
    {  
        throw new ApplicationException(string.Format(  
            CultureInfo.InvariantCulture,   
            "{0} is an invalid culture name for currency as it is too long.",   
            cultureNameMaxSize));  
    }  
  
    String paddedName = cultureName.PadRight(cultureNameMaxSize, '\0');  
    for (int i = 0; i < cultureNameMaxSize; i++)  
    {  
        w.Write(paddedName[i]);  
    }  
  
    // Normalize decimal value to two places  
    currencyValue = Decimal.Floor(currencyValue * 100) / 100;  
    w.Write(currencyValue);  
}  
public void Read(System.IO.BinaryReader r)  
{  
    char[] name = r.ReadChars(cultureNameMaxSize);  
    int stringEnd = Array.IndexOf(name, '\0');  
  
    if (stringEnd == 0)  
    {  
        cultureName = null;  
        return;  
    }  
  
    cultureName = new String(name, 0, stringEnd);  
    currencyValue = r.ReadDecimal();  
}  
```  
  
 Для получения полного кода для `Currency` определяемого пользователем ТИПА, см. в разделе [образцы SQL Server Database Engine](http://msftengprodsamples.codeplex.com/).  
  
## <a name="see-also"></a>См. также  
 [Создание определяемого пользователем типа](creating-user-defined-types.md)  
  
  
