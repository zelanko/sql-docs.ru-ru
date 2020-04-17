---
title: Кодирование пользовательских типов (ru) Документы Майкрософт
description: В этом примере показано, как реализовать UDT для использования в базе данных сервера S'L. Он реализует UDT как структуру.
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
ms.openlocfilehash: a9d51cc0c33c8b656df176baa606a88a542ca4bc
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81486964"
---
# <a name="creating-user-defined-types---coding"></a>Создание определяемых пользователем типов — программирование
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При разработке определяемого пользователем типа необходимо реализовать различные функциональные возможности в зависимости от того, реализуется ли определяемый пользователем тип в виде класса или структуры, а также от выбранных параметров формата и сериализации.  
  
 Пример в этом разделе иллюстрирует реализацию **точки** UDT в качестве **структуры** (или **структуры** в visual Basic). **Точка** UDT состоит из X и Y координаты реализованы в качестве процедур свойства.  
  
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
  
 В пространстве имен **Microsoft.SqlServer.Server** содержатся объекты, необходимые для различных атрибутов вашего UDT, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] а в пространстве имен **System.Data.SqlTypes** содержатся классы, представляющие типы нативных данных, доступные для сборки. Разумеется, конкретной сборке для правильной работы могут понадобиться и другие пространства имен. **Point** UDT также использует пространство имен **System.Text** для работы со строками.  
  
> [!NOTE]  
>  Объекты базы данных Visual C, такие как UDTs, компилируются с **/clr:pure,** не поддерживаются для выполнения.  
  
## <a name="specifying-attributes"></a>Определение атрибутов  
 Атрибуты определяют, каким образом сериализация используется для создания хранимых представлений определяемых пользователем типов, а также для передачи таких типов клиенту по значению.  
  
 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** не требуется. Необязательный атрибут **Serializable** является необязательным. Вы также можете указать **Microsoft.SqlServer.Server.SqlFacetAttribute** предоставить информацию о типе возврата UDT. Дополнительные сведения см. в статье [Пользовательские атрибуты процедур CLR](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md).  
  
### <a name="point-udt-attributes"></a>Атрибуты определяемого пользователем типа Point  
 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** устанавливает формат хранения для **точки** UDT для **родной**. **IsByteOrdered** настроен на **истину,** что гарантирует, что результаты сравнения являются такими же в сервере S'L, как если бы то же сравнение имело место в управляемом коде. UDT реализует **интерфейс System.Data.SqlTypes.INullable,** чтобы сделать UDT недействительным.  
  
 Следующий фрагмент кода показывает атрибуты для **точки** UDT.  
  
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
 Помимо задания необходимых атрибутов для сборок определяемый пользователем тип должен также поддерживать допустимость значений NULL. Загруженные UDT [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не осведомлены об этом, но для того, чтобы UDT распознал нулевую стоимость, UDT должен реализовать интерфейс **System.Data.SqlTypes.INullable.**  
  
 Необходимо создать свойство под названием **IsNull,** которое необходимо для определения того, является ли значение нулевым из кода CLR. При обнаружении в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра определяемого пользователем типа со значением NULL происходит его сохранение с использованием обычных методов работы со значениями NULL. Сервер не теряет времени на сериализацию и десериализацию определяемого пользователем типа, обнаруживая, что это не требуется, а также не расходует место для хранения определяемого пользователем типа со значением NULL. Проверка на наличие значений NULL проводится каждый раз, когда значение определяемого пользователем типа передается из среды CLR, а это означает, что конструкция языка [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL для проверки определяемых пользователем типов на значения NULL всегда должна работать. Свойство **IsNull** также используется сервером для проверки того, является ли экземпляр недействительным. Если сервер определил, что определяемый пользователем тип равен NULL, то может использовать собственные методы работы со значениями NULL.  
  
 Получить **()** метод **IsNull** не является специальным случаем в любом случае. Если переменная ** \@** **точка** p является **Null,** то ** \@p.IsNull** будет, по умолчанию, оценивать его до "NULL", а не "1". Это связано с тем, что атрибут **SlMethod (OnNullCall)** **метода IsNull получает()** по умолчанию ложные. Поскольку объект **является null,** когда запрашиваемый объект не десериализован, метод не вызывается, и значение "NULL" по умолчанию возвращается.  
  
### <a name="example"></a>Пример  
 В следующем примере переменная `is_Null` является закрытой и хранит состояние NULL экземпляра определяемого пользователем типа. В программном коде должно поддерживаться соответствующее значение переменной `is_Null`. UDT также должен иметь статическое свойство под названием **Null,** которое возвращает экземпляр нулевой стоимости UDT. Это позволяет возвращать значение NULL в определяемом пользователем типе, если экземпляр в базе данных действительно равен NULL.  
  
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
  
### <a name="is-null-vs-isnull"></a>IS NULL и IsNull  
 Рассмотрим таблицу, содержащую баллы схемы (id int, location Point), где **точка** является CLR UDT, и следующие запросы:  
  
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
  
 Оба запроса возвращают идолы точек с местами, не являемыми**нулевыми.** В запросе 1 используется нормальная обработка значений NULL, а десериализация определяемых пользователем типов не требуется. Запрос 2, с другой стороны, должен десериализировать каждый объект, не**являйся нулем,** и вызывать сярприз в CLR для получения стоимости свойства **IsNull.** Очевидно, что использование **IS NULL** будет проявлять лучшую производительность и никогда не должно быть оснований для чтения **isNull** собственности UDT из [!INCLUDE[tsql](../../includes/tsql-md.md)] кода.  
  
 Итак, что толку от свойства **IsNull?** Во-первых, необходимо определить, является ли значение **нулем** из кода CLR. Во-вторых, серверу нужен способ проверить, является ли экземпляр **Null,** поэтому это свойство используется сервером. После того, как он определяет, что это **null,** то он может использовать свой родной null обработки для обработки его.  
  
## <a name="implementing-the-parse-method"></a>Реализация синтаксического анализа  
 Методы **Parse** и **ToString** позволяют конверсии в и из строк представления UDT. Метод **Parse** позволяет преобразовывать строку в UDT. Он должен быть объявлен **статическим** (или **общим** в Visual Basic) и взять параметр типа **System.Data.SqlTypes.SqlString.**  
  
 Следующий код реализует метод **Parse** для **точки** UDT, которая отделяет координаты X и Y. Метод **Parse** имеет один аргумент типа **System.Data.SqlTypes.SqlString**и предполагает, что значения X и Y поставляются в виде строки, делимитированной запятой. Установка атрибута **Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall** на **ложную** не позволяет методу **Parse** вызываться из нулевой экземпляра Point.  
  
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
 Метод **ToString** преобразует **значение Point** UDT в значение строки. В этом случае строка "NULL" возвращается для экземпляра Null типа **точки.** Метод **ToString** меняет метод **Parse,** используя **System.Text.StringBuilder** для возврата **запятой,** разграниченной System.String, состоящей из значений Координат X и Y. Поскольку **InvokeIfReceiverIsNull** по умолчанию не подделает ложное значение, проверка нулевого экземпляра **Point** не нужна.  
  
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
 **Точка** UDT предоставляет X и Y координаты, которые реализуются как общедоступные свойства чтения записи типа **System.Int32**.  
  
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
  
 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName** собственности **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** позволяет предоставить имя метода проверки, что сервер работает, когда данные назначены на UDT или преобразованы в UDT. **ВалидацияMethodName** также называется во время выполнения утилиты bcp, BULK INSERT, DBCC CHECKDB, DBCC CHECKFILEGROUP, DBCC CHECKTABLE, распределенного запроса и табулярного потока данных (TDS) удаленного вызова процедуры (RPC). Значение по умолчанию для **ValidationMethodName** является нулевым, что указывает на отсутствие метода проверки.  
  
### <a name="example"></a>Пример  
 Следующий фрагмент кода показывает декларацию для класса **Point,** которая определяет **валидациюMethodName** **ValidatePoint.**  
  
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
  
 Метод проверки может иметь какую-либо область и должен **вернуться,** если значение является действительным, и **ложным** в противном случае. Если метод возвращает **ложное** или бросает исключение, значение считается недействительным и ошибка возникает.  
  
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
  
 Необходимо явно вызвать метод проверки от сеттеров свойств и метод **Parse,** если требуется, чтобы метод проверки выполнялся во всех ситуациях. Это не является требованием и в некоторых случаях даже нежелательно.  
  
### <a name="parse-validation-example"></a>Пример проверки при синтаксическом анализе  
 Чтобы убедиться, что метод **ValidatePoint** вызывается в классе **Point,** необходимо вызвать его из метода **Parse** и из процедур свойств, которые устанавливают значения X и Y координат. Следующий фрагмент кода показывает, как вызвать метод проверки **ValidatePoint** из **функции Parse.**  
  
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
 Следующий фрагмент кода показывает, как вызвать метод проверки **ValidatePoint** из процедур свойств, которые устанавливают координаты X и Y.  
  
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
 При реализации методов определяемого пользователем типа следует учитывать возможность изменения алгоритма в будущем. Если такая возможность имеется, то следует создать отдельный класс для методов, используемых определяемым пользователем типом. Если алгоритм изменится, можно будет перекомпилировать класс с новым кодом и загрузить сборку в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], не затрагивая определяемый пользователем тип. Во многих случаях определяемые пользователем типы можно загружать заново с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY, но это может вызвать проблемы с существующими данными. Например, **в валютном** UDT, включенном в выборочную базу данных **AdventureWorks,** используется функция **ConvertCurrency** для конвертации валютных значений, которая реализуется в отдельном классе. Возможно, что в будущем алгоритмы преобразования изменятся непредсказуемым образом или потребуются новые функциональные возможности. Отделение функции **ConvertCurrency** от реализации **Currency** UDT обеспечивает большую гибкость при планировании будущих изменений.  
  
### <a name="example"></a>Пример  
 Класс **Point** содержит три простых метода расчета расстояния: **Расстояние**, **расстояние и** **расстояниеFromXY**. Каждый возвращает **двойное** вычисление расстояния от **точки** до нуля, расстояние от указанной точки до **точки**и расстояние от указанных Координат X и Y до **точки.** **Расстояние** и **расстояниеОт** каждого вызова **DistanceFromXY**, и продемонстрировать, как использовать различные аргументы для каждого метода.  
  
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
 В классе **Microsoft.SqlServer.Server.SqlMethodAttribute** предусмотрены пользовательские атрибуты, которые могут быть использованы для обозначения определений метода, чтобы указать детерминизм, поведение нулевой вызова и указать, является ли метод мутатором. Предполагается, что эти свойства имеют определенные значения по умолчанию, а настраиваемый атрибут используется только тогда, когда необходимо задать другое значение.  
  
> [!NOTE]  
>  Класс **SqlMethodAttribute** наследует от класса **SqlFunctionAttribute,** поэтому **SqlMethodAttribute** наследует поля **FillRowMethodName** и **TableDefinition** от **SqlFunctionAttribute.** Это подразумевает, что существует возможность написать возвращающий табличное значение метод, который не является вариантом. Метод компилирует и развертывает сборку, но ошибка в типе **IEnumerable** return возникает во времени выполнения\<со следующим сообщением: "Метод, свойство или поле "имя>" в классе "класс\<>" в сборке ">\<сборки" имеет недействительным тип возврата".  
  
 В следующей таблице описаны некоторые из соответствующих свойств **Microsoft.SqlServer.Server.SqlMethodAttribute,** которые могут быть использованы в методах UDT, и перечислены их значения по умолчанию.  
  
 DataAccess  
 Указывает, что функция производит доступ к пользовательским данным, хранимым в локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию **DataAccessKind**. **Нет**.  
  
 IsDeterministic  
 Указывает, производит ли функция одни и те же выходные значения при одинаковых наборах входных значений и одинаковых состояниях базы данных. По умолчанию является **ложным**.  
  
 IsMutator  
 Указывает, вызывает ли метод изменение состояния экземпляра определяемого пользователем типа. По умолчанию является **ложным**.  
  
 IsPrecise  
 Указывает, содержит ли функция вычисления с потерей точности (например, операции с плавающей запятой). По умолчанию является **ложным**.  
  
 OnNullCall  
 Указывает, вызывается ли метод, если в качестве ссылки на входные аргументы заданы значения NULL. По умолчанию **это правда**.  
  
### <a name="example"></a>Пример  
 Свойство **Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator** позволяет пометить метод, позволяющий изменять состояние экземпляра UDT. Язык [!INCLUDE[tsql](../../includes/tsql-md.md)] не позволяет задать два свойства определяемого пользователем типа в предложении SET одной инструкции UPDATE. Однако можно создать метод-мутатор, изменяющий два члена определяемого пользователем типа сразу.  
  
> [!NOTE]  
>  Методы-мутаторы в запросах не допускаются. Их можно вызывать только в инструкциях присваивания или изменения данных. Если метод, помеченный как мутатор, не **возвращается недействительным** (или не является **Sub** в Visual Basic), CREATE TYPE не справляется с ошибкой.  
  
 Следующее утверждение предполагает существование **треугольников** UDT, который имеет метод **поворота.** Следующее [!INCLUDE[tsql](../../includes/tsql-md.md)] утверждение обновления вызывает метод **Поворота:**  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 Метод **«Поворот»** украшен установкой атрибута **SqlMethod** **IsMutator,** **чтобы** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] он мог пометить метод мутатора как метод мутатора. Код также устанавливает **OnNullCall** на **ложные,** что указывает на сервер, что метод возвращает нулевую ссылку (**Ничего** в Visual Basic), если какой-либо из параметров ввода являются нулевыми ссылками.  
  
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
 При реализации UDT с пользовательским форматом необходимо реализовать методы **чтения** и **записи,** которые реализуют интерфейс Microsoft.SqlServer.Server.IBinarySerialize для обработки сериализации и десериализации данных UDT. Вы также должны указать свойство **MaxByteSize** **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**.  
  
### <a name="the-currency-udt"></a>Определяемый пользователем тип Currency  
 **Валюта** UDT включена с образцами CLR, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]которые [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]могут быть установлены с , начиная с .  
  
 **Валюта** UDT поддерживает обработку денежных сумм в денежной системе конкретной культуры. Вы должны определить два поля: **строка** для **CultureInfo**, который определяет, кто выпустил валюту (en-us, например) и **десятичная** для **CurrencyValue**, сумма денег.  
  
 Хотя он не используется сервером для выполнения сравнений, **Валюта** UDT реализует **интерфейс System.IComparable,** который предоставляет единый метод, **System.IComparable.CompareTo**. Он используется на клиенте в ситуациях, когда необходимо провести точное сравнение или сортировку значений денежных сумм внутри культур.  
  
 Код, работающий в среде CLR, сравнивает культуры отдельно от значений суммы. Для кода на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] сравнение определяется следующими действиями.  
  
1.  Установите атрибут **IsByteOrdered** на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] истину, который говорит использовать сохраняющиеся двоичные представления на диске для сравнения.  
  
2.  Используйте метод **Write** для **Currency** UDT, чтобы определить, как UDT сохраняется на диске [!INCLUDE[tsql](../../includes/tsql-md.md)] и, следовательно, как значения UDT сравниваются и упорядочены для операций.  
  
3.  Сохранить **валюту** UDT с помощью следующего двоичного формата:  

    1.  Культура сохраняется в виде строки в кодировке UTF-16 для байтов 0-19 с дополнением нулевыми символами справа.  
  
    2.  Байты с 20 и выше используются для сохранения десятичного значения денежной суммы.  
  
 Дополнение нужно для того, чтобы гарантировать полное отделение значения культуры от значения суммы. Тогда при сравнении одного значения определяемого пользователем типа с другим в коде [!INCLUDE[tsql](../../includes/tsql-md.md)] значение одной культуры можно будет побайтно сравнить со значением другой культуры, а значения байтов одной денежной суммы — со значениями байтов другой денежной суммы.  
  
 Для полного перечисления кода для **Валюты** UDT, следуйте инструкциям по установке образцов CLR в [образцах движков базы данных сервера S'L.](https://msftengprodsamples.codeplex.com/)  
  
### <a name="currency-attributes"></a>Атрибуты Currency  
 **Валюта** UDT определяется со следующими атрибутами.  
  
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
 При выборе формата сериализации **UserDefined** необходимо реализовать интерфейс **IBinarySerialize** и создать свои собственные методы **чтения** и **записи.** Следующие процедуры от **валюты** UDT использовать **System.IO.BinaryReader** и **System.IO.BinaryWriter** читать и писать в UDT.  
  
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
  
 Для полного перечисления кода для **Валюты** UDT, [см.](https://msftengprodsamples.codeplex.com/)  
  
## <a name="see-also"></a>См. также:  
 [Создание определяемого пользователем типа](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
