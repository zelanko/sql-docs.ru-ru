---
title: Изменение данных больших значений (max) в ADO.NET
description: Описание работы с типами данных больших значений.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 9acbd8fb795fe1a14e77e5d746f729d37c11cc8d
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896685"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>Изменение данных больших значений (max) в ADO.NET

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Типы данных LOB — это данные, размер которых превышает максимальный размер строки в 8 килобайт (КБ). SQL Server представляет описатель `max` для типов данных `varchar`, `nvarchar` и `varbinary`, позволяющий сохранять значения размером до 2^32 байт. В столбцах таблицы и переменных Transact-SQL может быть указан тип данных `varchar(max)`, `nvarchar(max)` или `varbinary(max)`. В ADO.NET новые типы данных `max` можно выбрать с помощью объекта `DataReader`, а также их можно задавать в качестве значений входных и выходных параметров без какой-либо специальной обработки. В случае типов больших значений `varchar` данные могут извлекаться и обновляться постепенно.  
  
Типы данных `max` можно использовать для сравнения как переменные языка Transact-SQL, а также для объединения. Кроме того, их можно использовать в предложениях DISTINCT, ORDER BY и GROUP BY инструкции SELECT, а также в агрегатах, объединениях и вложенных запросах.

Дополнительные сведения о типах данных больших значений см. в [этой статье](https://go.microsoft.com/fwlink/?LinkId=120498) в электронной документации на SQL Server.
  
## <a name="large-value-type-restrictions"></a>Ограничения типов больших значений  
Приведенные ниже ограничения применяются к типам данных `max`, которые не существуют для типов данных меньших значений.  
  
- `sql_variant` не может содержать тип данных больших значений `varchar`.  
  
- Столбцы с данными больших значений `varchar` нельзя указать в качестве ключевого столбца в индексе. Они разрешены в столбце, включенном в некластеризованный индекс.  
  
- Столбцы с данными больших значений `varchar` нельзя использовать в качестве ключевых столбцов секционирования.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Работа с типами больших значений в Transact-SQL  
Функция Transact-SQL `OPENROWSET` — это одноразовый метод подключения и получения доступа к удаленным данным. Из предложения FROM запроса можно ссылаться на функцию `OPENROWSET` как на имя таблицы. На нее можно также ссылаться как на целевую таблицу в инструкции INSERT, UPDATE или DELETE.  
  
Функция `OPENROWSET` содержит поставщик наборов строк `BULK`, который позволяет считывать данные напрямую из файла без загрузки в целевую таблицу. Это позволяет использовать функцию `OPENROWSET` в обычной инструкции INSERT SELECT.  
  
С помощью аргументов параметра `OPENROWSET BULK` можно управлять началом и концом считывания данных, отладкой ошибок и способом представления полученных данных. Например, можно указать, что файл с данными будет считан как однострочный или как набор строк типа `varbinary`, `varchar` или `nvarchar` в один столбец. Полное описание синтаксиса и параметров см. в электронной документации на SQL Server.  
  
Следующий пример вставляет фотографию в таблицу ProductPhoto в примере базы данных AdventureWorks. При использовании поставщика `BULK OPENROWSET` необходимо указывать именованный список столбцов, даже если значения не вставляются в каждый столбец. В этом случае первичный ключ определяется как столбец идентификаторов и может быть опущен в списке столбцов. Обратите внимание, что вам необходимо лишь указать имя корреляции (в данном случае ThumbnailPhoto) в конце инструкции `OPENROWSET`. Оно соотносится со столбцом в таблице `ProductPhoto`, в которую загружается файл.  
  
```sql
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,   
    ThumbnailPhotoFilePath,   
    LargePhoto,   
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET   
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a>Обновление данных при помощи синтаксиса UPDATE .WRITE  
В инструкции Transact-SQL UPDATE имеется новый синтаксис WRITE, используемый для изменения содержимого столбцов `varchar(max)`, `nvarchar(max)` или `varbinary(max)`. Он позволяет выполнять частичные обновления данных. Синтаксис UPDATE .WRITE указан здесь в сокращенной форме.  
  
UPDATE  
  
{ *\<object>* }  
  
SET  
  
{ *column_name* = { .WRITE ( *выражение* , @Offset , @Length ) }  
  
Метод WRITE указывает, что часть значения *column_name* будет изменена. Выражение является значением, которое будет скопировано в поле *column_name*. Аргумент `@Offset` является начальной точкой записи выражения, а аргумент `@Length` — длиной изменяемой секции в столбце.  
  
|Если|То|  
|--------|----------|  
|Для выражения задано значение NULL.|Аргумент `@Length` не обрабатывается, а значение в поле *column_name* усекается в соответствии с указанным аргументом `@Offset`.|  
|`@Offset` равно NULL|Операция обновления добавляет выражение в конец существующего значения *column_name*, и аргумент `@Length` не обрабатывается.|  
|Значение аргумента `@Offset` больше, чем длина значения аргумента column_name.|SQL Server возвращает ошибку.|  
|`@Length` равно NULL|Операция обновления удаляет все данные, начиная с позиции `@Offset` до конца значения `column_name`.|  
  
> [!NOTE]
>  Ни `@Offset`, ни `@Length` не может быть отрицательным числом.  
  
## <a name="example"></a>Пример  
Этот пример Transact-SQL обновляет частичное значение в DocumentSummary, столбце `nvarchar(max)` таблицы Document в базе данных AdventureWorks. Слово components заменяется словом features, при этом указывается новое слово, начальное смещение слова, заменяемого в исходном тексте, и число заменяемых символов (длина). Этот пример содержит инструкцию SELECT перед и после инструкции UPDATE для сравнения результатов.  
  
```sql
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO   
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a>Работа с типами больших значений в ADO.NET  
В ADO.NET можно работать с типами больших значений, указав их в качестве параметров <xref:Microsoft.Data.SqlClient.SqlParameter> в <xref:Microsoft.Data.SqlClient.SqlDataReader> для возврата результирующего набора либо воспользовавшись объектом <xref:Microsoft.Data.SqlClient.SqlDataAdapter> для заполнения набора `DataSet`/`DataTable`. Обработка типов больших значений и связанных с ними типов данных меньших значений ничем не отличается.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Извлечение данных с помощью GetSqlBytes  
Метод `GetSqlBytes` класса <xref:Microsoft.Data.SqlClient.SqlDataReader> можно использовать для извлечения содержимого столбца `varbinary(max)`. В приведенном ниже фрагменте кода предполагается наличие объекта <xref:Microsoft.Data.SqlClient.SqlCommand> с именем `cmd`, который выбирает данные `varbinary(max)` из таблицы, и объекта <xref:Microsoft.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает данные в качестве класса <xref:System.Data.SqlTypes.SqlBytes>.  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Извлечение данных с помощью GetSqlChars  
Метод `GetSqlChars` класса <xref:Microsoft.Data.SqlClient.SqlDataReader> можно использовать для извлечения содержимого столбца `varchar(max)` или `nvarchar(max)`. В приведенном ниже фрагменте кода предполагается наличие объекта <xref:Microsoft.Data.SqlClient.SqlCommand> с именем `cmd`, который выбирает данные `nvarchar(max)` из таблицы, и объекта <xref:Microsoft.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает данные.   
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>Извлечение данных GetSqlBinary  
Метод `GetSqlBinary` класса <xref:Microsoft.Data.SqlClient.SqlDataReader> можно использовать для извлечения содержимого столбца `varbinary(max)`. В приведенном ниже фрагменте кода предполагается наличие объекта <xref:Microsoft.Data.SqlClient.SqlCommand> с именем `cmd`, который выбирает данные `varbinary(max)` из таблицы, и объекта <xref:Microsoft.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает данные в качестве потока <xref:System.Data.SqlTypes.SqlBinary>.  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a>Извлечение данных с помощью GetBytes  
Метод `GetBytes` класса <xref:Microsoft.Data.SqlClient.SqlDataReader> считывает поток байтов с указанного смещения столбца в массив байтов, начиная с указанного смещения массива. В приведенном ниже фрагменте кода предполагается наличие объекта <xref:Microsoft.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает байты в массив байтов. Обратите внимание, что в отличие от `GetSqlBytes` для метода `GetBytes` требуется размер для буфера массива.  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a>Извлечение данных с помощью GetValue  
Метод `GetValue` класса <xref:Microsoft.Data.SqlClient.SqlDataReader> считывает значение из указанного смещения столбца в массив. В приведенном ниже фрагменте кода предполагается наличие объекта <xref:Microsoft.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает двоичные данные из первого смещения столбца, а затем данные строки из второго смещения столбца.  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a>Преобразование типов больших значений в типы CLR  
Вы можете преобразовать содержимое столбца `varchar(max)` или `nvarchar(max)` с использованием любого метода преобразования строк, например `ToString`. В приведенном ниже фрагменте кода предполагается наличие объекта <xref:Microsoft.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает данные.  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a>Пример  
Приведенный ниже код извлекает имя и объект `LargePhoto` из таблицы `ProductPhoto` в базе данных `AdventureWorks` и сохраняет его в файле. Сборку необходимо скомпилировать со ссылкой на пространство имен <xref:System.Drawing>.  Метод <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> класса <xref:Microsoft.Data.SqlClient.SqlDataReader> возвращает объект <xref:System.Data.SqlTypes.SqlBytes>, который предоставляет свойство `Stream`. Код использует его для создания нового объекта `Bitmap`, а затем сохраняет его как изображение `ImageFormat` в формате Gif.  
  
[!code-csharp[DataWorks SqlBytes_Stream#1](~/../sqlclient/doc/samples/SqlBytes_Stream.cs#1)]
  
## <a name="using-large-value-type-parameters"></a>Использование параметров типа больших значений  
Типы больших значений можно использовать в объектах <xref:Microsoft.Data.SqlClient.SqlParameter> точно так же, как и типы меньших значений в объектах <xref:Microsoft.Data.SqlClient.SqlParameter>. Типы больших значений можно извлекать в виде значений <xref:Microsoft.Data.SqlClient.SqlParameter>, как показано в следующем примере. В коде предполагается существование в примере базы данных AdventureWorks приведенной ниже хранимой процедуры GetDocumentSummary. Хранимая процедура принимает входной параметр @DocumentID и возвращает содержимое столбца DocumentSummary в выходной параметр @DocumentSummary.  
  
```sql
CREATE PROCEDURE GetDocumentSummary   
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a>Пример  
Код ADO.NET создает объекты <xref:Microsoft.Data.SqlClient.SqlConnection> и <xref:Microsoft.Data.SqlClient.SqlCommand> для выполнения хранимой процедуры GetDocumentSummary и извлечения сводки документа, которая сохраняется как тип больших значений. Код передает значение входному параметру @DocumentID и отображает результаты, переданные обратно в выходной параметр @DocumentSummary, в окне консоли.  
  
[!code-csharp[DataWorks SqlParameter_Value#1](~/../sqlclient/doc/samples/SqlParameter_Value.cs#1)]
  
## <a name="next-steps"></a>Дальнейшие действия
- [Двоичные данные и данные больших значений SQL Server](sql-server-binary-large-value-data.md)
- [Операции с данными SQL Server в ADO.NET](sql-server-data-operations.md)
