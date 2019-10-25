---
title: Изменение данных больших значений (max) в ADO.NET
description: Описывает работу с типами данных больших значений.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: fac55eb25f89ced173683d5ed5d4334c2fcde975
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452120"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>Изменение данных больших значений (max) в ADO.NET

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Типы данных LOB — это данные, размер которых превышает максимальный размер строки в 8 килобайт (КБ). SQL Server представляет описатель `max` для типов данных `varchar`, `nvarchar` и `varbinary`, позволяющий сохранять значения размером до 2^32 байт. Столбцы таблицы и переменные Transact-SQL могут указывать типы данных `varchar(max)`, `nvarchar(max)` или `varbinary(max)`. В ADO.NET новые типы данных `max` можно выбрать с помощью объекта `DataReader`, а также их можно задавать в качестве значений входных и выходных параметров без какой-либо специальной обработки. Для больших `varchar` типов данных данные могут извлекаться и обновляться постепенно.  
  
Типы данных `max` можно использовать для сравнения как переменные языка Transact-SQL, а также для объединения. Они также могут использоваться в предложениях DISTINCT, ORDER BY, GROUP BY инструкции SELECT, а также в статистических выражениях, объединениях и вложенных запросах.

Дополнительные сведения о типах данных больших значений см. в разделе [Использование типов данных больших значений](https://go.microsoft.com/fwlink/?LinkId=120498) из электронная документация на SQL Server.
  
## <a name="large-value-type-restrictions"></a>Ограничения типов больших значений  
К `max` типам данных, которые не существуют для типов данных меньшего размера, применяются следующие ограничения.  
  
- `sql_variant` не может содержать тип данных Large `varchar`.  
  
- Большие `varchar` столбцы не могут быть указаны в индексе в качестве ключевого столбца. Они разрешены в столбце, входящем в состав некластеризованного индекса.  
  
- Столбцы с большими `varchar` не могут использоваться в качестве ключевых столбцов секционирования.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Работа с типами больших значений в Transact-SQL  
Функция `OPENROWSET` Transact-SQL является одноразовым методом подключения к удаленным данным и доступа к ним. Из предложения FROM запроса можно ссылаться на функцию `OPENROWSET` как на имя таблицы. На нее можно также ссылаться как на целевую таблицу в инструкции INSERT, UPDATE или DELETE.  
  
Функция `OPENROWSET` включает в себя `BULK` поставщика наборов строк, который позволяет считывать данные непосредственно из файла, не загружая данные в целевую таблицу. Это позволяет использовать функцию `OPENROWSET` в обычной инструкции INSERT SELECT.  
  
С помощью аргументов параметра `OPENROWSET BULK` можно управлять началом и концом считывания данных, отладкой ошибок и способом представления полученных данных. Например, можно указать, что файл с данными будет считан как однострочный или как набор строк типа `varbinary`, `varchar` или `nvarchar` в один столбец. Полный синтаксис и параметры см. в разделе электронная документация на SQL Server.  
  
В следующем примере фотография вставляется в таблицу ProductPhoto образца базы данных AdventureWorks. При использовании поставщика `BULK OPENROWSET` необходимо указывать именованный список столбцов, даже если значения не вставляются в каждый столбец. Первичный ключ в этом случае определяется как столбец идентификаторов и может быть опущен в списке столбцов. Обратите внимание, что необходимо также указать корреляционное имя в конце оператора `OPENROWSET`, который в данном случае является ThumbnailPhoto. Это соотносится со столбцом в `ProductPhoto` таблице, в которую загружается файл.  
  
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
В инструкции Transact-SQL UPDATE имеется новый синтаксис WRITE для изменения содержимого столбцов `varchar(max)`, `nvarchar(max)` или `varbinary(max)`. Это позволяет выполнять частичные обновления данных. ОБНОВЛЕНИЕ. Синтаксис записи показан здесь в сокращенном виде:  
  
UPDATE  
  
{ *\<object>* }  
  
SET  
  
{ *column_name* = {. WRITE ( *выражение* , @Offset, @Length)}  
  
Метод WRITE указывает, что часть значения *column_name* будет изменена. Выражение является значением, которое будет скопировано в поле *column_name*. Аргумент `@Offset` является начальной точкой записи выражения, а аргумент `@Length` — длиной изменяемой секции в столбце.  
  
|Если оператор|То|  
|--------|----------|  
|Для выражения задано значение NULL|Аргумент `@Length` не обрабатывается, а значение в поле *column_name* усекается в соответствии с указанным аргументом `@Offset`.|  
|`@Offset` равно NULL|Операция обновления добавляет выражение в конец существующего значения *column_name*, и аргумент `@Length` не обрабатывается.|  
|`@Offset` больше, чем длина значения column_name|SQL Server возвращает ошибку.|  
|`@Length` равно NULL|Операция обновления удаляет все данные, начиная с позиции `@Offset` до конца значения `column_name`.|  
  
> [!NOTE]
>  Ни `@Offset`, ни `@Length` не могут быть отрицательным числом.  
  
## <a name="example"></a>Пример  
Этот пример Transact-SQL обновляет частичное значение в DocumentSummary, столбец `nvarchar(max)` в таблице документа в базе данных AdventureWorks. Слово components заменяется словом features, при этом указывается новое слово, начальное смещение слова, заменяемого в исходном тексте, и число заменяемых символов (длина). Пример включает инструкции SELECT до и после инструкции UPDATE для сравнения результатов.  
  
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
В ADO.NET можно работать с типами больших значений, указав их в качестве параметров <xref:Microsoft.Data.SqlClient.SqlParameter> в <xref:Microsoft.Data.SqlClient.SqlDataReader> для возврата результирующего набора либо воспользовавшись объектом <xref:Microsoft.Data.SqlClient.SqlDataAdapter> для заполнения набора `DataSet`/`DataTable`. Между тем, как вы работаете с типом больших значений и связанным с ним типом данных с меньшим значением, нет никакой разницы.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Использование Жетсклбитес для получения данных  
Для получения содержимого `varbinary(max)` столбца можно использовать метод `GetSqlBytes` <xref:Microsoft.Data.SqlClient.SqlDataReader>. В следующем фрагменте кода предполагается, что объект <xref:Microsoft.Data.SqlClient.SqlCommand> с именем `cmd`, выбирающий `varbinary(max)` данные из таблицы и объект <xref:Microsoft.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает данные как <xref:System.Data.SqlTypes.SqlBytes>.  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Использование Жетсклчарс для получения данных  
Метод `GetSqlChars` <xref:Microsoft.Data.SqlClient.SqlDataReader> можно использовать для получения содержимого столбца `varchar(max)` или `nvarchar(max)`. В следующем фрагменте кода предполагается, что объект <xref:Microsoft.Data.SqlClient.SqlCommand> с именем `cmd`, выбирающий `nvarchar(max)` данные из таблицы и объект <xref:Microsoft.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает данные.   
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>Использование Жетсклбинари для получения данных  
Для получения содержимого `varbinary(max)` столбца можно использовать метод `GetSqlBinary` <xref:Microsoft.Data.SqlClient.SqlDataReader>. В следующем фрагменте кода предполагается, что объект <xref:Microsoft.Data.SqlClient.SqlCommand> с именем `cmd`, выбирающий `varbinary(max)` данные из таблицы и объект <xref:Microsoft.Data.SqlClient.SqlDataReader> с именем `reader`, который получает данные в виде <xref:System.Data.SqlTypes.SqlBinary> потока.  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a>Получение данных с помощью GetBytes  
Метод `GetBytes` <xref:Microsoft.Data.SqlClient.SqlDataReader> считывает поток байтов из указанного смещения столбца в массив байтов, начиная с указанного смещения массива. В следующем фрагменте кода предполагается, что объект <xref:Microsoft.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает байты в массив байтов. Обратите внимание, что, в отличие от `GetSqlBytes`, `GetBytes` требуется размер буфера массива.  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a>Использование функции GetValue для получения данных  
Метод `GetValue` <xref:Microsoft.Data.SqlClient.SqlDataReader> считывает значение из указанного смещения столбца в массив. В следующем фрагменте кода предполагается, что <xref:Microsoft.Data.SqlClient.SqlDataReader> объект с именем `reader`, который извлекает двоичные данные из первого смещения столбца, а затем строковые данные из второго смещения столбца.  
  
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
Содержимое `varchar(max)` или `nvarchar(max)` столбца можно преобразовать с помощью любого из методов преобразования строк, например `ToString`. В следующем фрагменте кода предполагается, что объект <xref:Microsoft.Data.SqlClient.SqlDataReader> с именем `reader`, который извлекает данные.  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a>Пример  
Следующий код извлекает имя и объект `LargePhoto` из таблицы `ProductPhoto` в базе данных `AdventureWorks` и сохраняет ее в файл. Сборка должна быть скомпилирована со ссылкой на пространство имен <xref:System.Drawing>.  Метод <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> <xref:Microsoft.Data.SqlClient.SqlDataReader> возвращает объект <xref:System.Data.SqlTypes.SqlBytes>, предоставляющий свойство `Stream`. Код использует его для создания нового объекта `Bitmap`, а затем сохраняет его как изображение `ImageFormat` в формате Gif.  
  
[!code-csharp[DataWorks SqlBytes_Stream#1](~/../sqlclient/doc/samples/SqlBytes_Stream.cs#1)]
  
## <a name="using-large-value-type-parameters"></a>Использование параметров типа больших значений  
Типы больших значений можно использовать в <xref:Microsoft.Data.SqlClient.SqlParameter> объектах так же, как и типы меньшего значения в <xref:Microsoft.Data.SqlClient.SqlParameter> объектах. Типы больших значений можно извлекать в виде значений <xref:Microsoft.Data.SqlClient.SqlParameter>, как показано в следующем примере. В коде предполагается, что в образце базы данных AdventureWorks существует следующая хранимая процедура Жетдокументсуммари. Хранимая процедура принимает входной параметр @DocumentID и возвращает содержимое столбца DocumentSummary в выходной параметр @DocumentSummary.  
  
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
Код ADO.NET создает <xref:Microsoft.Data.SqlClient.SqlConnection> и <xref:Microsoft.Data.SqlClient.SqlCommand> объекты для выполнения хранимой процедуры Жетдокументсуммари и получения сводки документа, которая хранится в виде типа больших значений. Код передает значение входному параметру @DocumentID и отображает результаты, переданные обратно в выходной параметр @DocumentSummary, в окне консоли.  
  
[!code-csharp[DataWorks SqlParameter_Value#1](~/../sqlclient/doc/samples/SqlParameter_Value.cs#1)]
  
## <a name="next-steps"></a>Дальнейшие действия
- [Двоичные данные и данные больших значений SQL Server](sql-server-binary-large-value-data.md)
- [Операции с данными SQL Server в ADO.NET](sql-server-data-operations.md)
