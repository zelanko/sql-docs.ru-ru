---
title: Определяемые пользователем типы кодирования | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: a0647d1e0f7dd082b3ce3aab668d8af8d5673efb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795772"
---
# <a name="creating-user-defined-types---coding"></a>Создание определяемых пользователем типов — программирование
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При разработке определяемого пользователем типа необходимо реализовать различные функциональные возможности в зависимости от того, реализуется ли определяемый пользователем тип в виде класса или структуры, а также от выбранных параметров формата и сериализации.  
  
 В примере в этом разделе показана реализация **точки** определяемый пользователем тип как **структуры** (или **структуры** в Visual Basic). **Точки** определяемого пользователем ТИПА состоит из X и Y-координаты реализован как процедуры свойств.  
  
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
  
 **Microsoft.SqlServer.Server** пространство имен содержит объекты, необходимые для различных атрибутов определяемого пользователем ТИПА и **System.Data.SqlTypes** пространство имен содержит классы, представляющие [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]собственных типов данных для сборки. Разумеется, конкретной сборке для правильной работы могут понадобиться и другие пространства имен. **Точки** определяемого пользователем ТИПА также использует **System.Text** пространство имен для работы со строками.  
  
> [!NOTE]  
>  Визуальных объектов базы данных C++, такие как определяемые пользователем типы, скомпилированные с использованием **/CLR: pure** не поддерживаются для выполнения.  
  
## <a name="specifying-attributes"></a>Определение атрибутов  
 Атрибуты определяют, каким образом сериализация используется для создания хранимых представлений определяемых пользователем типов, а также для передачи таких типов клиенту по значению.  
  
 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** является обязательным. **Serializable** атрибут является необязательным. Можно также указать **Microsoft.SqlServer.Server.SqlFacetAttribute** для предоставления сведений о типе возвращаемого значения определяемого пользователем типа. Дополнительные сведения см. в статье [Пользовательские атрибуты процедур CLR](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md).  
  
### <a name="point-udt-attributes"></a>Атрибуты определяемого пользователем типа Point  
 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** задает формат хранения **точки** определяемого пользователем ТИПА **собственного**. **IsByteOrdered** присваивается **true**, а это гарантирует, что результаты сравнения будут соответствующим образом в SQL Server как, если же бы сравнение проводилось в управляемом коде. Определяемый пользователем тип реализует **System.Data.SqlTypes.INullable** интерфейс сообщить null определяемого пользователем ТИПА.  
  
 В следующем фрагменте кода показаны атрибуты для **точки** определяемого пользователем ТИПА.  
  
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
 Помимо задания необходимых атрибутов для сборок определяемый пользователем тип должен также поддерживать допустимость значений NULL. Определяемые пользователем типы загружаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживают значение null, но чтобы определяемый пользователем тип распознавал значение null, определяемый пользователем тип должен реализовывать **System.Data.SqlTypes.INullable** интерфейс.  
  
 Необходимо создать свойство с именем **IsNull**, который необходим для определения, является ли значение null из кода CLR. При обнаружении в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра определяемого пользователем типа со значением NULL происходит его сохранение с использованием обычных методов работы со значениями NULL. Сервер не теряет времени на сериализацию и десериализацию определяемого пользователем типа, обнаруживая, что это не требуется, а также не расходует место для хранения определяемого пользователем типа со значением NULL. Проверка на наличие значений NULL проводится каждый раз, когда значение определяемого пользователем типа передается из среды CLR, а это означает, что конструкция языка [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL для проверки определяемых пользователем типов на значения NULL всегда должна работать. **IsNull** свойство также используется сервером для проверки, имеет ли экземпляр значение null. Если сервер определил, что определяемый пользователем тип равен NULL, то может использовать собственные методы работы со значениями NULL.  
  
 **Get()** метод **IsNull** не является специальным случаем любым способом. Если **точки** переменной **@p** — **Null**, затем **@p.IsNull** по умолчанию принимает значение «NULL», не «1». Это обусловлено **SqlMethod(OnNullCall)** атрибут **IsNull get()** метод по умолчанию — false. Так как объект **Null**, когда свойство запрашивается объект не десериализуется, метод не вызывается и возвращается значение по умолчанию «NULL».  
  
### <a name="example"></a>Пример  
 В следующем примере переменная `is_Null` является закрытой и хранит состояние NULL экземпляра определяемого пользователем типа. В программном коде должно поддерживаться соответствующее значение переменной `is_Null`. Определяемый пользователем тип должен также иметь статическое свойство с именем **Null** , возвращает значение null экземпляр определяемого пользователем типа. Это позволяет возвращать значение NULL в определяемом пользователем типе, если экземпляр в базе данных действительно равен NULL.  
  
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
 Рассмотрим таблицу, содержащую схему Points (id int, location Point), где **точки** определяемого пользователем ТИПА CLR, а также следующие запросы:  
  
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
  
 Оба запроса возвращают идентификаторы точек с отличным от**Null** расположений. В запросе 1 используется нормальная обработка значений NULL, а десериализация определяемых пользователем типов не требуется. Запрос 2, с другой стороны, приходится обеспечивать десериализацию каждого отличных**Null** объекта и вызывать среду CLR для получения значений **IsNull** свойство. Очевидно, что использование **IS NULL** будет достигается более высокая производительность и никогда не следует прибегать к чтению **IsNull** свойства определяемого пользователем типа из [!INCLUDE[tsql](../../includes/tsql-md.md)] кода.  
  
 Таким образом, что такое использование **IsNull** свойство? Во-первых, необходимо, чтобы определить, является ли значение **Null** из кода CLR. Во-вторых, серверу необходим способ, позволяющий проверить, является ли экземпляр **Null**, поэтому это свойство используется на сервере. После его определяет его **Null**, она сможет использовать его собственного обработка null для ее обработки.  
  
## <a name="implementing-the-parse-method"></a>Реализация синтаксического анализа  
 **Проанализировать** и **ToString** методы позволяют для преобразования в и из строковых представлений определяемого пользователем типа. **Проанализировать** метод позволяет строка преобразуется в определяемый пользователем тип. Он должен быть объявлен как **статический** (или **Shared** в Visual Basic) и принимать параметр типа **System.Data.SqlTypes.SqlString**.  
  
 В следующем коде реализуется **проанализировать** метод **точки** определяемого пользователем ТИПА, который позволяет отделить координаты X и Y. **Проанализировать** метод имеет один аргумент типа **System.Data.SqlTypes.SqlString**и предполагается, что значения X и Y передаются как строка с разделителями запятыми. Установка **Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall** атрибут **false** предотвращает **проанализировать** вызов из неопределенный экземпляр метода Точка.  
  
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
 **ToString** метод преобразует **точки** определяемого пользователем ТИПА в строковое значение. В этом случае возвращается строка «NULL» для экземпляра Null **точки** типа. **ToString** обращает метод **проанализировать** метод с помощью **System.Text.StringBuilder** для возврата, с разделителями запятыми **System.String**состоящий из значения координат X и Y. Так как **InvokeIfReceiverIsNull** по умолчанию — false, проверка неопределенный экземпляр **точки** не требуется.  
  
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
 **Точки** определяемого пользователем ТИПА представляет координаты X и Y, которые реализованы как открытые свойства чтения и записи типа **System.Int32**.  
  
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
  
 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName** свойство **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** позволяет указать имя метода проверки, что сервер выполняется при запуске назначенный определяемому пользователем ТИПУ или преобразуется в определяемый пользователем тип данных. **ValidationMethodName** также вызывается во время выполнения программы bcp, BULK INSERT, DBCC CHECKDB, DBCC CHECKFILEGROUP, DBCC CHECKTABLE, распределенного запроса и табличных данных (TDS) удаленной процедуры вызова (RPC) операций потока. Значение по умолчанию для **ValidationMethodName** имеет значение null, указывающее, что нет способа проверки.  
  
### <a name="example"></a>Пример  
 В следующем фрагменте кода показано объявление **точки** класса, определяющего **ValidationMethodName** из **ValidatePoint**.  
  
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
  
 Метод проверки может иметь любую область и должен возвращать **true** Если значение является допустимым, и **false** в противном случае. Если метод возвращает **false** или создает исключение, оно интерпретируется как не является допустимым и ошибка возникает.  
  
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
  
 Необходимо явно вызывать метод проверки из методов задания свойств и **проанализировать** метод, если требуется, чтобы метод проверки, чтобы во всех ситуациях. Это не является требованием и в некоторых случаях даже нежелательно.  
  
### <a name="parse-validation-example"></a>Пример проверки при синтаксическом анализе  
 Чтобы убедиться, что **ValidatePoint** метод вызывается в **точки** класса, необходимо вызвать его из **проанализировать** метод и из процедур свойства X и Y значения координат. В следующем фрагменте кода показан способ вызова **ValidatePoint** метод проверки **проанализировать** функции.  
  
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
 В следующем фрагменте кода показан способ вызова **ValidatePoint** метод проверки из процедур свойств, заданных координат X и Y.  
  
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
 При реализации методов определяемого пользователем типа следует учитывать возможность изменения алгоритма в будущем. Если такая возможность имеется, то следует создать отдельный класс для методов, используемых определяемым пользователем типом. Если алгоритм изменится, можно будет перекомпилировать класс с новым кодом и загрузить сборку в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], не затрагивая определяемый пользователем тип. Во многих случаях определяемые пользователем типы можно загружать заново с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY, но это может вызвать проблемы с существующими данными. Например **валюты** определяемого пользователем ТИПА в состав **AdventureWorks** примере используется база данных **ConvertCurrency** функции для преобразования значений, который реализуется в отдельном классе. Возможно, что в будущем алгоритмы преобразования изменятся непредсказуемым образом или потребуются новые функциональные возможности. Отделение **ConvertCurrency** функции из **валюты** реализации определяемого пользователем ТИПА обеспечивает большую гибкость при планировании для будущих изменений.  
  
### <a name="example"></a>Пример  
 **Точки** класс содержит три простых метода вычисления расстояния: **расстояние**, **DistanceFrom** и **DistanceFromXY**. Каждая возвращает **двойные** равное расстоянию от **точки** нулю, расстояние от указанной точки до **точки**, и от заданных координат X и Y Чтобы **точки**. **Расстояние** и **DistanceFrom** каждый вызов **DistanceFromXY**и демонстрируется использование различных аргументов для каждого метода.  
  
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
 **Microsoft.SqlServer.Server.SqlMethodAttribute** класс предоставляет настраиваемые атрибуты, которые могут использоваться для обозначения определения методов детерминированный, задать на поведение вызова null, а также указать, является ли метод мутатора. Предполагается, что эти свойства имеют определенные значения по умолчанию, а настраиваемый атрибут используется только тогда, когда необходимо задать другое значение.  
  
> [!NOTE]  
>  **SqlMethodAttribute** класс наследует от **SqlFunctionAttribute** класса, поэтому **SqlMethodAttribute** наследует **FillRowMethodName** и **TableDefinition** поля из **SqlFunctionAttribute**. Это подразумевает, что существует возможность написать возвращающий табличное значение метод, который не является вариантом. Метод компилируется, и сборка развертывается, но ошибка о **IEnumerable** возвращают тип возникает во время выполнения со следующим сообщением: «метод, свойство или поле "\<имя >" в классе\<класса > "в сборке"\<сборки > "имеет недопустимый возвращаемый тип.»  
  
 В следующей таблице описаны некоторые соответствующего **Microsoft.SqlServer.Server.SqlMethodAttribute** свойства, которые можно использовать в методов определяемого пользователем ТИПА и перечисляются их значения по умолчанию.  
  
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
 **Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator** свойство позволяет пометить метод, который производит изменение состояния экземпляра определяемого пользователем типа. Язык [!INCLUDE[tsql](../../includes/tsql-md.md)] не позволяет задать два свойства определяемого пользователем типа в предложении SET одной инструкции UPDATE. Однако можно создать метод-мутатор, изменяющий два члена определяемого пользователем типа сразу.  
  
> [!NOTE]  
>  Методы-мутаторы в запросах не допускаются. Их можно вызывать только в инструкциях присваивания или изменения данных. Если метод, помеченный как мутатор, не возвращает **void** (или не **Sub** в Visual Basic), CREATE TYPE завершится с ошибкой.  
  
 Следующая инструкция подразумевает наличие **треугольники** определяемый пользователем тип, имеющий **Поворот** метод. Следующие [!INCLUDE[tsql](../../includes/tsql-md.md)] вызывает инструкцию update **Поворот** метод:  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 **Поворот** метод дополняется **SqlMethod** параметр атрибута **IsMutator** для **true** таким образом, чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно пометить Этот метод как метод мутатора. В коде также задается **OnNullCall** для **false**, который указывает серверу, что метод возвращает пустую ссылку (**ничего не** в Visual Basic) Если любой из входных данных параметры являются пустыми ссылками.  
  
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
 При реализации определяемого пользователем ТИПА в определяемом пользователем формате, необходимо реализовать **чтения** и **записи** методы, реализующие интерфейс Microsoft.SqlServer.Server.IBinarySerialize для сериализации и десериализация определяемого пользователем ТИПА данных. Необходимо также указать **MaxByteSize** свойство **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**.  
  
### <a name="the-currency-udt"></a>Определяемый пользователем тип Currency  
 **Валюты** определяемого пользователем ТИПА входит в состав образцов CLR, которые могут быть установлены с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 **Валюты** определяемый пользователем тип поддерживает обработку денежных сумм в денежной системе конкретной культуры. Необходимо определить два поля: **строка** для **CultureInfo**, задающее источник валюты (en-us, например) и **десятичное** для  **Currencyvalue, хранящее сумму**, представляющего денежные суммы.  
  
 Несмотря на то, что он не используется сервером для операций сравнения **валюты** определяемый пользователем тип реализует **System.IComparable** интерфейс, который предоставляет единственный метод,  **System.IComparable.CompareTo**. Он используется на клиенте в ситуациях, когда необходимо провести точное сравнение или сортировку значений денежных сумм внутри культур.  
  
 Код, работающий в среде CLR, сравнивает культуры отдельно от значений суммы. Для кода на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] сравнение определяется следующими действиями.  
  
1.  Задайте **IsByteOrdered** атрибута значение "true", который сообщает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для использования сохраненного двоичного представления на диске для сравнения.  
  
2.  Используйте **записи** метод **валюты** определяемого пользователем ТИПА, чтобы определить, каким образом сохраняется значение данного ТИПА на диске и поэтому как сравнение и Сортировка значений определяемого пользователем ТИПА [!INCLUDE[tsql](../../includes/tsql-md.md)] операций.  
  
3.  Сохранить **валюты** определяемого пользователем ТИПА, используя следующий двоичный формат:  
  
    1.  Культура сохраняется в виде строки в кодировке UTF-16 для байтов 0-19 с дополнением нулевыми символами справа.  
  
    2.  Байты с 20 и выше используются для сохранения десятичного значения денежной суммы.  
  
 Дополнение нужно для того, чтобы гарантировать полное отделение значения культуры от значения суммы. Тогда при сравнении одного значения определяемого пользователем типа с другим в коде [!INCLUDE[tsql](../../includes/tsql-md.md)] значение одной культуры можно будет побайтно сравнить со значением другой культуры, а значения байтов одной денежной суммы — со значениями байтов другой денежной суммы.  
  
 Для получения полного кода для **валюты** определяемого пользователем ТИПА, выполните инструкции по установке CLR образцов в [образцы SQL Server Database Engine](http://msftengprodsamples.codeplex.com/).  
  
### <a name="currency-attributes"></a>Атрибуты Currency  
 **Валюты** определяемого пользователем ТИПА определен со следующими атрибутами.  
  
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
 При выборе **UserDefined** формат сериализации, необходимо также реализовать **интерфейс IBinarySerialize** интерфейс и создать свой собственный **чтения** и **записи**  методы. Следующие процедуры из **валюты** использование определяемого пользователем ТИПА **System.IO.BinaryReader** и **System.IO.BinaryWriter** для чтения и записи на определяемый пользователем тип.  
  
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
  
 Для получения полного кода для **валюты** определяемого пользователем ТИПА, см. в разделе [образцы SQL Server Database Engine](http://msftengprodsamples.codeplex.com/).  
  
## <a name="see-also"></a>См. также  
 [Создание определяемого пользователем типа](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
