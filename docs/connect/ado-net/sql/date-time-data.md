---
title: Данных типа date и time
description: В этой статье описывается использование новых типов данных даты и времени, появившихся в SQL Server 2008.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 75d8b98726a758e0533053dbdf8d2e03b3bfdf0d
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896987"
---
# <a name="date-and-time-data"></a>Данных типа date и time

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

В SQL Server 2008 появились новые типы данных для обработки сведений о дате и времени. Новые типы данных включают в себя отдельные типы для даты и времени, а также расширенные типы данных с более высоким диапазоном, точностью и поддержкой часовых поясов. Поставщик данных Microsoft SqlClient для SQL Server (<xref:Microsoft.Data.SqlClient>) полностью поддерживает все новые возможности ядра СУБД SQL Server 2008. Чтобы использовать эти новые возможности с SqlClient, необходимо установить платформу .NET Framework 3.5 с пакетом обновления 1 (или более поздней версии) или .NET Core 1.0 (или более поздней версии).  
  
В версиях SQL Server, выпущенных до SQL Server 2008, было только два типа данных для работы с датами и временем: `datetime` и `smalldatetime`. Оба типа данных содержат как значение даты, так и значение времени, затрудняя работу только со значениями даты или времени. Кроме того, эти типы данных поддерживают только даты, наступившие после представления григорианского календаря в Англии в 1753 году. Другое ограничение заключается в том, что эти устаревшие типы данных не учитывают часовой пояс. Это затрудняет работу с данными, которые берутся из разных часовых поясов.  
  
Полная документация по типам данных SQL Server находится в электронной документации на SQL Server. Общие сведения о данных даты и времени см. в статье [Использование данных даты и времени](https://go.microsoft.com/fwlink/?LinkID=98361).
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Новые типы данных даты и времени в SQL Server 2008  
 В приведенной ниже таблице описаны новые типы данных даты и времени.  
  
|Тип данных SQL Server|Описание|  
|--------------------------|-----------------|  
|`date`|Тип данных `date` имеет диапазон от 1 января 01 года до 31 декабря 9999 года с точностью до дня. По умолчанию применяется значение 1 января 1900 г. Размер при хранении составляет 3 байта.|  
|`time`|Тип данных `time` сохраняет только значения времени, основанные на 24-часовом формате. Тип данных `time` имеет диапазон от 00:00:00.0000000 до 23:59:59.9999999 с точностью 100 наносекунд. Значение по умолчанию равно 00:00:00.0000000 (полночь). Тип данных `time` поддерживает определяемую пользователем точность в долях секунды, и размер хранения изменяется от 3 до 6 байт в зависимости от указанной точности.|  
|`datetime2`|Тип данных `datetime2` объединяет параметры диапазона и точности типов данных `date` и `time` в единый тип.<br /><br /> Значения по умолчанию и форматы строковых литералов совпадают с типами данных `date` и `time`.|  
|`datetimeoffset`|Тип данных `datetimeoffset` обладает всеми характеристиками типа `datetime2` с добавлением смещения часового пояса. Смещение часового пояса представлено в виде [+&#124;-] ЧЧ:ММ. ЧЧ — двузначное число от 00 до 14, представляющее количество часов в смещении часового пояса. Обозначение ММ состоит из двух цифр, представляющих дополнительное смещение часового пояса в минутах, и принимает значения от 00 до 59. Форматы времени поддерживаются с точностью до 100 наносекунд. Обязательный знак "+" или "-" указывает, добавлено ли или вычтено смещение часового пояса из времени в формате UTC (по Гринвичу) для получения местного времени.|  
  
> [!NOTE]
>  Дополнительные сведения об использовании `Type System Version` см. в разделе <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Формат и порядок даты  
То, как SQL Server анализирует значения даты и времени, зависит не только от версии системы типов и версии сервера, но также от параметров языка и формата по умолчанию для сервера. Строка даты, которая подходит для форматов даты одного языка, может быть нераспознаваемой, если запрос выполняется подключением, в котором используются другие язык и формат даты.  
  
Инструкция Transact-SQL SET LANGUAGE неявно устанавливает DATEFORMAT, который определяет порядок частей даты. Вы можете использовать инструкцию SET DATEFORMAT Transact-SQL в подключении для устранения неоднозначности значений даты путем упорядочения частей даты в порядке МДГ, ДМГ, ГМД, ГДМ, МГД или ДГМ.  
  
Если вы не укажете DATEFORMAT для подключения, SQL Server использует связанный с этим подключением язык по умолчанию. Например, строка даты "01/02/03" будет интерпретироваться как МДГ (2 января 2003 г.) на сервере с заданным языком "английский (США)" и как ДМГ (1 февраля 2003 г.) на сервере с заданным языком "английский (Великобритания)". Год определяется с помощью правила порогового года SQL Server, которое определяет пороговую дату для назначения значения столетия. Дополнительные сведения см. в разделе [Параметр отсечения двух цифр года](https://go.microsoft.com/fwlink/?LinkId=120473) электронной документации на SQL Server.  
  
> [!NOTE]
>  Формат даты ГДМ не поддерживается при преобразовании из формата строки в `date`, `time`, `datetime2` или `datetimeoffset`.  
  
Дополнительные сведения об интерпретации сервером SQL Server даты и времени см. в разделе [Использование данных даты и времени](https://go.microsoft.com/fwlink/?LinkID=98361) электронной документации на SQL Server 2008.  
  
## <a name="datetime-data-types-and-parameters"></a>Типы данных и параметры даты и времени  
Для поддержки новых типов данных даты и времени к свойству <xref:System.Data.SqlDbType> были добавлены следующие значения перечисления.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Можно указать тип данных <xref:Microsoft.Data.SqlClient.SqlParameter> с помощью одного из предшествующих перечислений <xref:System.Data.SqlDbType>. 

> [!NOTE]
> Вы не можете установить для свойства `DbType` параметра `SqlParameter` значение `SqlDbType.Date`.

Также можно указать тип объекта <xref:Microsoft.Data.SqlClient.SqlParameter> в общей форме, задав для свойства <xref:Microsoft.Data.SqlClient.SqlParameter.DbType%2A> объекта `SqlParameter` особое значение перечисления <xref:System.Data.DbType>. Для поддержки типов данных `datetime2` и `datetimeoffset` к свойству <xref:System.Data.DbType> были добавлены следующие значения перечисления.  
  
- DbType.DateTime2.  
  
- DbType.DateTimeOffset.  
  
Эти новые перечисления дополняют перечисления `Date`, `Time` и `DateTime`.  
  
Тип поставщика данных Microsoft SqlClient для объекта параметра выводится из типа .NET значения объекта параметра или из `DbType` объекта параметра. Для поддержки новых типов данных даты и времени не введено новых типов данных <xref:System.Data.SqlTypes>. В приведенной ниже таблице описаны сопоставления между типами данных даты и времени SQL Server 2008 и типами данных CLR.  
  
|Тип данных SQL Server|Тип .NET|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|Дата|System.DateTime|Дата|Дата|  
|time|System.TimeSpan|Time|Time|  
|datetime2|System.DateTime|datetime2|datetime2|  
|datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|DATETIME|System.DateTime|Дата и время|Дата и время|  
|smalldatetime|System.DateTime|Дата и время|Дата и время|  
  
### <a name="sqlparameter-properties"></a>Свойства SqlParameter  
 В приведенной ниже таблице описаны свойства `SqlParameter`, которые относятся к типам данных даты и времени.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.IsNullable%2A>|Возвращает или задает допустимость значений NULL. Во время отправки значения NULL на сервер нужно указать <xref:System.DBNull>, а не `null` (`Nothing` в Visual Basic). Дополнительные сведения о значении NULL базы данных см. в статье [Handling null values](handle-null-values.md) (Обработка значений NULL).|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Precision%2A>|Возвращает или задает максимальное количество цифр, используемых для представления значения. Этот параметр не учитывается для типов данных даты и времени.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Scale%2A>|Возвращает или задает число десятичных разрядов, до которых разрешается промежуток времени для `Time`, `DateTime2` и `DateTimeOffset`. Значение по умолчанию равно 0. Это означает, что фактический масштаб выводится из значения и отправляется на сервер.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Size%2A>|Не учитывается для типов данных даты и времени.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Value%2A>|Возвращает или задает значение параметра.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.SqlValue%2A>|Возвращает или задает значение параметра.|  
  
> [!NOTE]
>  Значения времени, которые меньше нуля, больше или равны 24 часам, вызовут исключение <xref:System.ArgumentException>.  
  
### <a name="creating-parameters"></a>Создание параметров  
Вы можете создать объект <xref:Microsoft.Data.SqlClient.SqlParameter>, используя его конструктор или добавив его в коллекцию <xref:Microsoft.Data.SqlClient.SqlCommand>.<xref:Microsoft.Data.SqlClient.SqlCommand.Parameters%2A> путем вызова метода `Add` элемента <xref:Microsoft.Data.SqlClient.SqlParameterCollection>. Метод `Add` будет принимать в качестве входных данных аргументы конструктора либо имеющийся объект параметра.  
  
В следующих разделах этой статьи приведены примеры того, как указать параметры даты и времени.
  
### <a name="date-example"></a>Пример даты  
В приведенном ниже фрагменте кода демонстрируется, как указать параметр `date`.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
### <a name="time-example"></a>Пример времени  
В приведенном ниже фрагменте кода демонстрируется, как указать параметр `time`.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a>Пример с Datetime2  
В приведенном ниже фрагменте кода показано, как указать параметр `datetime2` с частями даты и времени.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a>Пример с DateTimeOffSet  
В приведенном ниже фрагменте кода показано, как указать параметр `DateTimeOffSet` с датой, временем и смещением часового пояса равным нулю.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a>AddWithValue  
Вы также можете указать параметры, используя метод `AddWithValue` элемента <xref:Microsoft.Data.SqlClient.SqlCommand>, как показано в приведенном ниже фрагменте кода. Однако метод `AddWithValue` не позволяет указывать свойство <xref:Microsoft.Data.SqlClient.SqlParameter.DbType%2A> или <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> для параметра.  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
Параметр `@date` можно сопоставить типу данных `date`, `datetime` или `datetime2` на сервере. При работе с новыми типами данных `datetime` необходимо явно установить для свойства параметра <xref:System.Data.SqlDbType> тип данных экземпляра. Использование <xref:System.Data.SqlDbType.Variant> или неявное предоставление значений параметров может вызвать проблемы с обратной совместимостью с типами данных `datetime` и `smalldatetime`.  
  
В приведенной ниже таблице показано, какие типы `SqlDbTypes` выводятся из типов CLR.  
  
|Тип среды CLR|Выводимый тип SqlDbType|  
|--------------|------------------------|  
|Дата и время|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Извлечение данных даты и времени  
В следующей таблице описаны методы, используемые для получения значений даты и времени SQL Server 2008.  
  
|Метод SqlClient|Описание|  
|----------------------|-----------------|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Извлекает значение указанного столбца в виде структуры <xref:System.DateTime>.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Извлекает значение указанного столбца в виде структуры <xref:System.DateTimeOffset>.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Возвращает для поля тип, являющийся базовым типом конкретного поставщика. Возвращает для новых типов даты и времени те же типы, что и `GetFieldType`.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Возвращает значение указанного столбца. Возвращает для новых типов даты и времени те же типы, что и `GetValue`.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Извлекает значения в указанном массиве.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Извлекает значение столбца как тип <xref:System.Data.SqlTypes.SqlString>. <xref:System.InvalidCastException> возникает, если данные нельзя выразить в виде `SqlString`.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Извлекает данные столбца в качестве `SqlDbType` по умолчанию. Возвращает для новых типов даты и времени те же типы, что и `GetValue`.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Извлекает значения в указанном массиве.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetString%2A>|Возвращает значение столбца в виде строки, если Type System Version имеет значение SQL Server 2005. <xref:System.InvalidCastException> возникает, если данные нельзя выразить в качестве строки.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Извлекает значение указанного столбца в виде структуры <xref:System.TimeSpan>.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetValue%2A>|Извлекает значение указанного столбца в виде базового типа CLR.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetValues%2A>|Извлекает значения столбцов в массиве.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Возвращает класс <xref:System.Data.DataTable>, описывающий метаданные результирующего набора.|  
  
> [!NOTE]
>  Новые дата и время `SqlDbTypes` не поддерживаются для кода, выполняющегося в процессе на SQL Server. Если один из этих типов будет передан на сервер, возникнет исключение.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Определение значений даты и времени в качестве литералов  
Вы можете указать типы данных даты и времени, используя множество различных форматов строк литералов, которые SQL Server затем оценивает во время выполнения, преобразовывая их во внутренние структуры даты и времени. SQL Server распознает данные даты и времени, заключенные в одинарные кавычки ('). Некоторые форматы продемонстрированы в следующих примерах.  
  
- Буквенные форматы даты, такие как `'October 15, 2006'`.  
  
- Числовые форматы даты, такие как `'10/15/2006'`.  
  
- Неразделенные форматы строк, например строка `'20061015'`, которая будет интерпретироваться как 15 октября 2006 г., если вы используете формат даты по стандарту ISO.  
  
> [!NOTE]
>  Вы можете найти полную документацию по всем форматам строк литералов и другим функциям типов данных даты и времени в электронной документации на SQL Server.  
  
Значения времени, которые меньше нуля, больше или равны 24 часам, вызовут исключение <xref:System.ArgumentException>.  
  
## <a name="resources-in-sql-server-2008-books-online"></a>Ресурсы в электронной документации по SQL Server 2008  
Дополнительные сведения о работе со значениями даты и времени в SQL Server 2008 см. в приведенных ниже ресурсах электронной документации по SQL Server 2008.  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Типы данных и функции даты и времени (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|Приводятся общие сведения обо всех типах данных и функциях даты и времени в языке Transact-SQL.|  
|[Использование данных даты и времени](https://go.microsoft.com/fwlink/?LinkId=98361)|Приводятся сведения и даются примеры использования функций и типов данных даты и времени.|  
|[Типы данных (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98362)|Описывает системные типы данных в SQL Server 2008.|  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Типы данных SQL Server и ADO.NET](sql-server-data-types.md)
