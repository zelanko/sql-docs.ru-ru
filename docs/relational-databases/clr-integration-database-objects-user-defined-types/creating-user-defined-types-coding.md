---
title: Кодирование определяемых пользователем типов | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e94662043d3801cc7088533d7f0fbadd638bec5b
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874810"
---
# <a name="creating-user-defined-types---coding"></a>Создание определяемых пользователем типов — программирование
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При разработке определяемого пользователем типа необходимо реализовать различные функциональные возможности в зависимости от того, реализуется ли определяемый пользователем тип в виде класса или структуры, а также от выбранных параметров формата и сериализации.  
  
 Пример в этом разделе иллюстрирует реализацию определяемого пользователем типа **Point** как **структуры** (или **структуры** в Visual Basic). Определяемый пользователем тип **Point** состоит из координат X и Y, реализованных как процедуры свойств.  
  
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
  
 Пространство имен **Microsoft. SqlServer. Server** содержит объекты, необходимые для различных атрибутов определяемого пользователем типа, а пространство имен **System. Data. SqlTypes** содержит классы, представляющие [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственные типы данных, доступные для сборок. Разумеется, конкретной сборке для правильной работы могут понадобиться и другие пространства имен. Определяемый пользователем тип **Point** также использует пространство имен **System. Text** для работы со строками.  
  
> [!NOTE]  
>  Визуальные C++ объекты базы данных, такие как определяемые пользователем типы, скомпилированные с **параметром/clr: pure** , не поддерживаются для выполнения.  
  
## <a name="specifying-attributes"></a>Определение атрибутов  
 Атрибуты определяют, каким образом сериализация используется для создания хранимых представлений определяемых пользователем типов, а также для передачи таких типов клиенту по значению.  
  
 Объект **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute** является обязательным. Атрибут **Serializable** является необязательным. Можно также указать **Microsoft. SqlServer. Server. SqlFacetAttribute** , чтобы предоставить сведения о типе возвращаемого значения UDT. Дополнительные сведения см. в статье [Пользовательские атрибуты процедур CLR](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md).  
  
### <a name="point-udt-attributes"></a>Атрибуты определяемого пользователем типа Point  
 Объект **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute** задает формат хранения для определяемого пользователем типа **Point** в **native**. **IsByteOrdered** имеет значение **true**, что гарантирует, что результаты сравнения одинаковы в SQL Server, как если бы сравнение выполнялось в управляемом коде. Определяемый пользователем тип реализует интерфейс **System. Data. SqlTypes. интерфейс INullable** , чтобы иметь возможность использовать определяемый пользователем тип NULL.  
  
 В следующем фрагменте кода показаны атрибуты для определяемого пользователем типа **Point** .  
  
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
 Помимо задания необходимых атрибутов для сборок определяемый пользователем тип должен также поддерживать допустимость значений NULL. Определяемые пользователем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы, загруженные в, поддерживают значение null, но чтобы определяемый пользователем тип мог распознать значение null, определяемый пользователем тип должен реализовывать интерфейс **System. Data. SqlTypes. интерфейс INullable** .  
  
 Необходимо создать свойство с именем **IsNull**, которое требуется для определения того, имеет ли значение NULL в коде CLR. При обнаружении в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра определяемого пользователем типа со значением NULL происходит его сохранение с использованием обычных методов работы со значениями NULL. Сервер не теряет времени на сериализацию и десериализацию определяемого пользователем типа, обнаруживая, что это не требуется, а также не расходует место для хранения определяемого пользователем типа со значением NULL. Проверка на наличие значений NULL проводится каждый раз, когда значение определяемого пользователем типа передается из среды CLR, а это означает, что конструкция языка [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL для проверки определяемых пользователем типов на значения NULL всегда должна работать. Свойство **IsNull** также используется сервером для проверки того, имеет ли экземпляр значение null. Если сервер определил, что определяемый пользователем тип равен NULL, то может использовать собственные методы работы со значениями NULL.  
  
 Метод **Get ()** функции **IsNull** не имеет особого представления. Если  **переменная\@** **Point** p имеет **значение NULL**, то функция  **\@p. IsNull** по умолчанию будет иметь значение "null", а не "1". Это обусловлено тем, что атрибут **склмесод (OnNullCall)** метода **IsNull Get ()** по умолчанию имеет значение false. Поскольку объект имеет **значение NULL**, то при запросе свойства объект не десериализуется, метод не вызывается и возвращается значение по умолчанию "null".  
  
### <a name="example"></a>Пример  
 В следующем примере переменная `is_Null` является закрытой и хранит состояние NULL экземпляра определяемого пользователем типа. В программном коде должно поддерживаться соответствующее значение переменной `is_Null`. Определяемый пользователем тип также должен иметь статическое свойство с именем **null** , которое возвращает экземпляр определяемого пользователем типа со значением NULL. Это позволяет возвращать значение NULL в определяемом пользователем типе, если экземпляр в базе данных действительно равен NULL.  
  
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
  
### <a name="is-null-vs-isnull"></a>ИМЕЕТ значение NULL или IsNull  
 Рассмотрим таблицу, содержащую точки схемы (идентификатор int, точка расположения), где **Point** — определяемый пользователем тип CLR и следующие запросы:  
  
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
  
 Оба запроса возвращают идентификаторы точек с расположениями, отличными от**null** . В запросе 1 используется нормальная обработка значений NULL, а десериализация определяемых пользователем типов не требуется. С другой стороны, запрос 2 должен выполнить десериализацию каждого объекта, отличного от**null** , и вызвать среду CLR, чтобы получить значение свойства **IsNull** . Очевидно, что использование параметра **равно NULL** обеспечит лучшую производительность и никогда не должен быть причиной считывания свойства **IsNull** определяемого пользователем типа из [!INCLUDE[tsql](../../includes/tsql-md.md)] кода.  
  
 Итак, каково использование свойства **IsNull** ? Во-первых, необходимо определить, имеет ли значение **null** в коде CLR. Во-вторых, серверу требуется способ проверки того, имеет ли экземпляр **значение NULL**, поэтому это свойство используется сервером. После того как он определит, что он равен **null**, он может использовать собственную обработку NULL для ее обработки.  
  
## <a name="implementing-the-parse-method"></a>Реализация синтаксического анализа  
 Методы **Parse** и **ToString** позволяют выполнять преобразования в строковые представления определяемого пользователем типа и из него. Метод **Parse** позволяет преобразовать строку в определяемый пользователем тип. Он должен быть объявлен как **статический** (или **совместно использоваться** в Visual Basic) и принимать параметр типа **System. Data. SqlTypes. SqlString**.  
  
 В следующем коде реализуется метод **Parse** для определяемого пользователем типа **Point** , который отделяет координаты X и Y. Метод **Parse** имеет единственный аргумент типа **System. Data. SqlTypes. SqlString**и предполагает, что значения X и Y предоставляются в виде строки с разделителями-запятыми. Установка атрибута **Microsoft. SqlServer. Server. склмесодаттрибуте. OnNullCall** в **значение false** предотвращает вызов метода **Parse** из экземпляра Point, имеющего значение null.  
  
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
 Метод **ToString** преобразует определяемый пользователем тип **Point** в строковое значение. В этом случае строка "NULL" возвращается для пустого экземпляра типа **Point** . Метод **ToString** обращается к методу **Parse** , используя **System. Text. StringBuilder** для возврата **строки** с разделителями-запятыми, состоящей из значений координат X и Y. Так как **инвокеифрецеивериснулл** по умолчанию имеет значение false, проверка экземпляра со значением **null не требуется** .  
  
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
 Определяемый пользователем тип **Point** предоставляет координаты X и Y, которые реализуются как открытые свойства для чтения и записи типа **System. Int32**.  
  
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
 При работе с определяемым пользователем типом компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] автоматически преобразовывает двоичные значения в значения определяемого пользователем типа. Этот процесс преобразования включает в себя проверку соответствия значений формату сериализации и проверку того, что значения могут быть десериализованы правильно. Это гарантирует, что значение можно преобразовать обратно в двоичную форму. В случае определяемого пользователем типа с заданным порядком байтов это также гарантирует, что результирующее двоичное значение совпадет с исходным. Благодаря этому предотвращается сохранение недопустимых значений в базе данных. В некоторых случаях такой уровень проверки недостаточен. Если значения определяемого пользователем типа должны находиться в определенной области или диапазоне, то может потребоваться дополнительная проверка. Например, для определяемого пользователем типа, реализующего дату, может потребоваться, чтобы день был положительным числом, попадающим в определенный диапазон допустимых значений.  
  
 Свойство **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute. Валидатионмесоднаме** **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute** позволяет указать имя метода проверки, выполняемого сервером. когда данные присваиваются определяемому пользователем типу или преобразуются в определяемый пользователем тип. **Валидатионмесоднаме** также вызывается во время выполнения программы bcp, BULK INSERT, DBCC CHECKDB, DBCC CHECKFILEGROUP, DBCC CHECKTABLE, распределенного запроса и операций удаленного вызова процедур (RPC) потока табличных данных (TDS). Значение по умолчанию для **валидатионмесоднаме** равно null, что означает отсутствие метода проверки.  
  
### <a name="example"></a>Пример  
 В следующем фрагменте кода показано объявление класса **Point** , который указывает **валидатионмесоднаме** **ValidatePoint**.  
  
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
  
 Метод проверки может иметь любую область видимости и должен возвращать значение **true** , если оно является допустимым, и **false** в противном случае. Если метод возвращает значение **false** или создает исключение, значение считается недопустимым и возникает ошибка.  
  
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
  
 Необходимо явно вызвать метод проверки из методов задания свойств и метода **Parse** , если необходимо, чтобы метод проверки выполнялся во всех ситуациях. Это не является требованием и в некоторых случаях даже нежелательно.  
  
### <a name="parse-validation-example"></a>Пример проверки при синтаксическом анализе  
 Чтобы обеспечить вызов метода **ValidatePoint** в классе **Point** , необходимо вызвать его из метода **Parse** и из процедур свойств, которые задают значения координат X и Y. В следующем фрагменте кода показано, как вызвать метод проверки **ValidatePoint** из функции **Parse** .  
  
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
 В следующем фрагменте кода показано, как вызвать метод проверки **ValidatePoint** из процедур свойств, устанавливающих координаты X и Y.  
  
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
 При реализации методов определяемого пользователем типа следует учитывать возможность изменения алгоритма в будущем. Если такая возможность имеется, то следует создать отдельный класс для методов, используемых определяемым пользователем типом. Если алгоритм изменится, можно будет перекомпилировать класс с новым кодом и загрузить сборку в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], не затрагивая определяемый пользователем тип. Во многих случаях определяемые пользователем типы можно загружать заново с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY, но это может вызвать проблемы с существующими данными. Например, определяемый пользователем тип **Currency** , входящий в образец базы данных **AdventureWorks** , использует функцию **ConvertCurrency** для преобразования значений валют, которые реализуются в отдельном классе. Возможно, что в будущем алгоритмы преобразования изменятся непредсказуемым образом или потребуются новые функциональные возможности. Отделение функции **ConvertCurrency** от реализации определяемого пользователем типа **Currency** обеспечивает большую гибкость при планировании будущих изменений.  
  
### <a name="example"></a>Пример  
 Класс **Point** содержит три простых метода для вычисления расстояния: **Distance**, **дистанцефром** и **дистанцефромкси**. Каждый из них возвращает **Двойное** Вычисление расстояния от **точки** к нулю, расстояние от указанной точки до **точки**, а расстояние от указанных координат X и Y до **точки**. **Distance** и **Дистанцефром** каждый вызов **дистанцефромкси**и демонстрирует, как использовать разные аргументы для каждого метода.  
  
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
 Класс **Microsoft. SqlServer. Server. склмесодаттрибуте** предоставляет настраиваемые атрибуты, которые можно использовать для пометки определения метода, чтобы указать детерминированность, поведение при вызове NULL и указать, является ли метод методом мутатора. Предполагается, что эти свойства имеют определенные значения по умолчанию, а настраиваемый атрибут используется только тогда, когда необходимо задать другое значение.  
  
> [!NOTE]  
>  Класс **склмесодаттрибуте** наследует от класса **SqlFunctionAttribute** , поэтому **склмесодаттрибуте** наследует поля **FillRowMethodName** и **TableDefinition** из **SqlFunctionAttribute**. Это подразумевает, что существует возможность написать возвращающий табличное значение метод, который не является вариантом. Метод компилируется, и сборка развертывается, но ошибка, связанная с типом возвращаемого значения **IEnumerable** , вызывается во время выполнения со следующим сообщением: "Метод, свойство или поле"\<имя > "в классе" класс "\<>" в сборке "\<сборка" > "имеет недопустимый тип возвращаемого значения".  
  
 В следующей таблице описаны некоторые из соответствующих свойств **Microsoft. SqlServer. Server. склмесодаттрибуте** , которые можно использовать в методах определяемого пользователем типа и перечислены их значения по умолчанию.  
  
 DataAccess  
 Указывает, что функция производит доступ к пользовательским данным, хранимым в локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Значение по умолчанию — **DataAccessKind**. **Нет**.  
  
 IsDeterministic  
 Указывает, производит ли функция одни и те же выходные значения при одинаковых наборах входных значений и одинаковых состояниях базы данных. Значение по умолчанию — **false**.  
  
 IsMutator  
 Указывает, вызывает ли метод изменение состояния экземпляра определяемого пользователем типа. Значение по умолчанию — **false**.  
  
 IsPrecise  
 Указывает, содержит ли функция вычисления с потерей точности (например, операции с плавающей запятой). Значение по умолчанию — **false**.  
  
 OnNullCall  
 Указывает, вызывается ли метод, если в качестве ссылки на входные аргументы заданы значения NULL. Значение по умолчанию — **true**.  
  
### <a name="example"></a>Пример  
 Свойство **Microsoft. SqlServer. Server. склмесодаттрибуте. мутатора** позволяет пометить метод, который позволяет изменить состояние экземпляра определяемого пользователем типа. Язык [!INCLUDE[tsql](../../includes/tsql-md.md)] не позволяет задать два свойства определяемого пользователем типа в предложении SET одной инструкции UPDATE. Однако можно создать метод-мутатор, изменяющий два члена определяемого пользователем типа сразу.  
  
> [!NOTE]  
>  Методы-мутаторы в запросах не допускаются. Их можно вызывать только в инструкциях присваивания или изменения данных. Если метод, помеченный как мутатора, не возвращает **значение void** (или **не является** подVisual Basic), то CREATE TYPE завершается ошибкой.  
  
 В следующей инструкции предполагается существование определяемого пользователем типа- **треугольника** с методом **вращения** . Следующая [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкция Update вызывает метод **вращения** :  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 Метод **вращения** снабжен атрибутом **склмесод** , устанавливая для параметра **IsTrue значение true** , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] чтобы можно было пометить метод как метод мутатора. Код также задает для **OnNullCall** **значение false**, которое указывает серверу, что метод возвращает пустую ссылку (**Nothing** в Visual Basic), если любой из входных параметров содержит ссылки null.  
  
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
 При реализации определяемого пользователем типа с пользовательским форматом необходимо реализовать методы **чтения** и **записи** , реализующие интерфейс Microsoft. SqlServer. Server. интерфейс IBinarySerialize, для управления сериализацией и десериализации данных определяемого пользователем типа. Необходимо также указать свойство **MaxByteSize** объекта **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute**.  
  
### <a name="the-currency-udt"></a>Определяемый пользователем тип Currency  
 Определяемый пользователем тип **Currency** входит в состав примеров среды CLR, которые могут [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]быть установлены с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], начиная с.  
  
 Определяемый пользователем тип **Currency** поддерживает обработку суммы денег в денежной системе определенного языка и региональных параметров. Необходимо определить два поля: **строку** для **CultureInfo**, которая указывает, кто выдавал валюту (например, EN-US), и **десятичное** значение для **курренцивалуе**— количество денег.  
  
 Хотя он не используется сервером для выполнения сравнений, определяемый пользователем тип **Currency** реализует интерфейс **System. IComparable** , предоставляющий единственный метод **System. IComparable. CompareTo**. Он используется на клиенте в ситуациях, когда необходимо провести точное сравнение или сортировку значений денежных сумм внутри культур.  
  
 Код, работающий в среде CLR, сравнивает культуры отдельно от значений суммы. Для кода на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] сравнение определяется следующими действиями.  
  
1.  Задайте для атрибута **IsByteOrdered** значение true, которое указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на использование сохраненного двоичного представления на диске для сравнения.  
  
2.  Используйте метод **Write** для определяемого пользователем типа **Currency** , чтобы определить, как определяемый пользователем тип сохраняется на диске и, следовательно, как значения определяемого пользователем типа сравниваются и упорядочиваются для [!INCLUDE[tsql](../../includes/tsql-md.md)] операций.  
  
3.  Сохраните определяемый пользователем тип **Currency** , используя следующий двоичный формат:  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

    1.  Культура сохраняется в виде строки в кодировке UTF-16 для байтов 0-19 с дополнением нулевыми символами справа.  
  
    2.  Байты с 20 и выше используются для сохранения десятичного значения денежной суммы.  
  
 Дополнение нужно для того, чтобы гарантировать полное отделение значения культуры от значения суммы. Тогда при сравнении одного значения определяемого пользователем типа с другим в коде [!INCLUDE[tsql](../../includes/tsql-md.md)] значение одной культуры можно будет побайтно сравнить со значением другой культуры, а значения байтов одной денежной суммы — со значениями байтов другой денежной суммы.  
  
 Чтобы получить полный листинг кода для определяемого пользователем типа **Currency** , следуйте инструкциям по установке примеров среды CLR в [SQL Server ядро СУБД Samples](https://msftengprodsamples.codeplex.com/).  
  
### <a name="currency-attributes"></a>Атрибуты Currency  
 Определяемый пользователем тип **Currency** определяется со следующими атрибутами.  
  
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
 При выборе формата сериализации **пользователяопределенные** необходимо также реализовать интерфейс **интерфейс IBinarySerialize** и создать собственные методы **чтения** и **записи** . Следующие процедуры из определяемого пользователем типа **Currency** используют **System. IO. BinaryReader** и **System. IO. BinaryWriter** для чтения и записи в определяемый пользователем тип.  
  
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
  
 Полный листинг кода для определяемого пользователем типа **Currency** см. в разделе [SQL Server ядро СУБД Samples](https://msftengprodsamples.codeplex.com/).  
  
## <a name="see-also"></a>См. также  
 [Создание определяемого пользователем типа](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
