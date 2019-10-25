---
title: Данных типа date и time
description: Описывает, как использовать новые типы данных даты и времени, появившиеся в SQL Server 2008.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 38626c6c726b9f45bd2d37d5deda480880556856
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452249"
---
# <a name="date-and-time-data"></a>Данных типа date и time

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

В SQL Server 2008 появились новые типы данных для обработки сведений о дате и времени. Новые типы данных включают отдельные типы для даты и времени, а также расширенные типы данных с более высоким диапазоном, точностью и поддержкой часовых поясов. Поставщик данных Microsoft SqlClient для SQL Server (<xref:Microsoft.Data.SqlClient>) обеспечивает полную поддержку всех новых функций ядро СУБД SQL Server 2008. Для использования этих новых функций с SqlClient необходимо установить .NET Framework 3,5 SP1 (или более поздней версии) или .NET Core 1,0 (или более поздней версии).  
  
В версиях SQL Server, выпущенных до SQL Server 2008, было только два типа данных для работы с датами и временем: `datetime` и `smalldatetime`. Оба типа данных содержат как значение даты, так и значение времени, затрудняя работу только со значениями даты или времени. Кроме того, эти типы данных поддерживают только даты, происходящие после введения григорианского календаря в Англия в 1753. Еще одно ограничение заключается в том, что эти старые типы данных не поддерживаются с учетом часового пояса, что затрудняет работу с данными, происходящими из нескольких часовых поясов.  
  
Полная документация по SQL Server типов данных доступна в электронная документация на SQL Server. См. раздел [использование данных даты и времени](https://go.microsoft.com/fwlink/?LinkID=98361) для получения данных о дате и времени на уровне входа.
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Новые типы данных даты и времени в SQL Server 2008  
 В следующей таблице описаны новые типы данных даты и времени.  
  
|Тип данных SQL Server|Описание|  
|--------------------------|-----------------|  
|`date`|Тип данных `date` имеет диапазон от 1 января 01 года до 31 декабря 9999 года с точностью до дня. Значение по умолчанию — 1 января 1900 г. Размер при хранении составляет 3 байта.|  
|`time`|Тип данных `time` сохраняет только значения времени, основанные на 24-часовом формате. Тип данных `time` имеет диапазон от 00:00:00.0000000 до 23:59:59.9999999 с точностью 100 наносекунд. Значение по умолчанию — 00:00:00.0000000 (полночь). Тип данных `time` поддерживает определяемую пользователем точность в долях секунды, и размер хранения изменяется от 3 до 6 байт в зависимости от указанной точности.|  
|`datetime2`|Тип данных `datetime2` объединяет диапазон и точность `date` и `time` типов данных в один тип данных.<br /><br /> Значения по умолчанию и форматы строковых литералов совпадают с типами данных `date` и `time`.|  
|`datetimeoffset`|Тип данных `datetimeoffset` обладает всеми характеристиками типа `datetime2` с добавлением смещения часового пояса. Смещение часового пояса представлено в виде [+&#124;-] ЧЧ:ММ. ЧЧ — двузначное число от 00 до 14, представляющее количество часов в смещении часового пояса. Обозначение ММ состоит из двух цифр, представляющих дополнительное смещение часового пояса в минутах, и принимает значения от 00 до 59. Форматы времени поддерживаются с точностью до 100 наносекунд. Обязательный знак + или-указывает, было ли смещение часового пояса добавлено или вычтено из времени UTC (универсальное время или время по Гринвичу) для получения местного времени.|  
  
> [!NOTE]
>  Дополнительные сведения об использовании `Type System Version` см. в разделе <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Формат даты и порядок даты  
SQL Server синтаксический анализ значений даты и времени зависит не только от версии системы типов и версии сервера, но также и от языка сервера по умолчанию и параметров формата. Строка даты, которая работает для форматов даты одного языка, может быть неопознана, если запрос выполняется соединением, использующим другой язык и параметр формата даты.  
  
Инструкция Transact-SQL SET LANGUAGE неявно устанавливает значение параметра DATEFORMAT, определяющее порядок частей даты. Инструкцию SET DATEFORMAT Transact-SQL можно использовать для соединения, чтобы устранить неоднозначность значений даты путем упорядочивания частей даты в MDY, DMY, ГМД, ГДМ, МГД или ДГМ.  
  
Если для соединения не указан параметр DATEFORMAT, SQL Server использует язык по умолчанию, связанный с подключением. Например, строка даты "01/02/03" будет интерпретироваться как MDY (2 января 2003) на сервере с параметром языка США английским, а DMY (1 февраля 2003) на сервере с параметром языка "Английский (Великобритания)". Год определяется с помощью правила "отсечение года SQL Server", которое определяет дату прекращения назначения для присвоения значения столетию. Дополнительные сведения см. в разделе [Параметр отсечения двух цифр года](https://go.microsoft.com/fwlink/?LinkId=120473) электронной документации на SQL Server.  
  
> [!NOTE]
>  Формат даты ГДМ не поддерживается при преобразовании из строкового формата в `date`, `time`, `datetime2` или `datetimeoffset`.  
  
Дополнительные сведения об интерпретации сервером SQL Server даты и времени см. в разделе [Использование данных даты и времени](https://go.microsoft.com/fwlink/?LinkID=98361) электронной документации на SQL Server 2008.  
  
## <a name="datetime-data-types-and-parameters"></a>Типы данных и параметры даты и времени  
Следующие перечисления были добавлены в <xref:System.Data.SqlDbType> для поддержки новых типов данных даты и времени.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Можно указать тип данных <xref:Microsoft.Data.SqlClient.SqlParameter> с помощью одного из предшествующих перечислений <xref:System.Data.SqlDbType>. 

> [!NOTE]
> Невозможно задать для свойства `DbType` `SqlParameter` значение `SqlDbType.Date`.

Также можно указать тип объекта <xref:Microsoft.Data.SqlClient.SqlParameter> в общей форме, задав для свойства <xref:Microsoft.Data.SqlClient.SqlParameter.DbType%2A> объекта `SqlParameter` особое значение перечисления <xref:System.Data.DbType>. Для поддержки типов данных `datetime2` и `datetimeoffset` к свойству <xref:System.Data.DbType> были добавлены следующие значения перечисления.  
  
- DbType. DateTime2  
  
- DbType. DateTimeOffset  
  
Эти новые перечисления дополняют перечисления `Date`, `Time` и `DateTime`.  
  
Тип поставщика данных SqlClient (Майкрософт) для объекта параметра выводится из типа .NET значения объекта параметра или из `DbType` объекта параметра. Новые типы данных <xref:System.Data.SqlTypes> для поддержки новых типов данных даты и времени не введены. В следующей таблице описаны сопоставления между типами данных SQL Server 2008 даты и времени и типами данных CLR.  
  
|Тип данных SQL Server|Тип .NET|System. Data. SqlDbType|System. Data. DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|Дата|System.DateTime|Дата|Дата|  
|time|System.TimeSpan|Time|Time|  
|datetime2|System.DateTime|datetime2|datetime2|  
|datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|DATETIME|System.DateTime|DateTime|DateTime|  
|smalldatetime|System.DateTime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>Свойства SqlParameter  
 В следующей таблице описаны `SqlParameter` свойства, относящиеся к типам данных даты и времени.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.IsNullable%2A>|Получение или установка значения, допускающего значение null. При отправке на сервер значения параметра NULL необходимо указать <xref:System.DBNull>, а не `null` (`Nothing` в Visual Basic). Дополнительные сведения об значениях NULL базы данных см. в разделе [Обработка значений NULL](handle-null-values.md).|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Precision%2A>|Возвращает или задает максимальное количество цифр, используемых для представления значения. Этот параметр игнорируется для типов данных даты и времени.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Scale%2A>|Возвращает или задает число десятичных разрядов, до которых разрешается промежуток времени для `Time`, `DateTime2` и `DateTimeOffset`. Значение по умолчанию — 0. Это означает, что фактический масштаб выводится из значения и отправляется на сервер.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Size%2A>|Игнорируется для типов данных даты и времени.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Value%2A>|Возвращает или задает значение параметра.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.SqlValue%2A>|Возвращает или задает значение параметра.|  
  
> [!NOTE]
>  Значения времени, которые меньше нуля или больше или равны 24 часам, вызовут <xref:System.ArgumentException>.  
  
### <a name="creating-parameters"></a>Создание параметров  
Объект <xref:Microsoft.Data.SqlClient.SqlParameter> можно создать с помощью его конструктора или путем добавления в <xref:Microsoft.Data.SqlClient.SqlCommand>. <xref:Microsoft.Data.SqlClient.SqlCommand.Parameters%2A> для сбора путем вызова метода `Add` <xref:Microsoft.Data.SqlClient.SqlParameterCollection>. Метод `Add` принимает в качестве входных аргументов либо аргументы конструктора, либо существующий объект Parameter.  
  
В следующих подразделах этого раздела приведены примеры указания параметров даты и времени.
  
### <a name="date-example"></a>Пример даты  
В следующем фрагменте кода показано, как указать параметр `date`.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
### <a name="time-example"></a>Пример времени  
В следующем фрагменте кода показано, как указать параметр `time`.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a>Пример с Datetime2  
В следующем фрагменте кода показано, как указать параметр `datetime2` с частями даты и времени.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a>Пример DateTimeOffSet  
В следующем фрагменте кода показано, как указать параметр `DateTimeOffSet` с датой, временем и смещением часового пояса, равным 0.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a>AddWithValue  
Параметры можно также указать с помощью метода `AddWithValue` <xref:Microsoft.Data.SqlClient.SqlCommand>, как показано в следующем фрагменте кода. Однако метод `AddWithValue` не позволяет указать <xref:Microsoft.Data.SqlClient.SqlParameter.DbType%2A> или <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> для параметра.  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
Параметр `@date` можно сопоставить типу данных `date`, `datetime` или `datetime2` на сервере. При работе с новыми типами данных `datetime` необходимо явно задать свойство <xref:System.Data.SqlDbType> параметра в качестве типа данных экземпляра. Использование <xref:System.Data.SqlDbType.Variant> или неявное указание значений параметров может привести к проблемам с обратной совместимостью с типами данных `datetime` и `smalldatetime`.  
  
В следующей таблице показано, какие `SqlDbTypes` выводятся из типов CLR.  
  
|Тип среды CLR|Выводимый SqlDbType|  
|--------------|------------------------|  
|DateTime|SqlDbType. DateTime|  
|TimeSpan|SqlDbType. Time|  
|DateTimeOffset|SqlDbType. DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Получение данных даты и времени  
В следующей таблице описаны методы, используемые для получения значений даты и времени SQL Server 2008.  
  
|Метод SqlClient|Описание|  
|----------------------|-----------------|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Извлекает значение указанного столбца в виде структуры <xref:System.DateTime>.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Извлекает значение указанного столбца в виде структуры <xref:System.DateTimeOffset>.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Возвращает тип, который является базовым типом конкретного поставщика для поля. Возвращает те же типы, что и `GetFieldType` для новых типов даты и времени.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Возвращает значение указанного столбца. Возвращает те же типы, что и `GetValue` для новых типов даты и времени.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Получает значения в указанном массиве.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Получает значение столбца в виде <xref:System.Data.SqlTypes.SqlString>. <xref:System.InvalidCastException> возникает, если данные не могут быть выражены как `SqlString`.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Извлекает данные столбца в качестве `SqlDbType` по умолчанию. Возвращает те же типы, что и `GetValue` для новых типов даты и времени.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Получает значения в указанном массиве.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetString%2A>|Возвращает значение столбца в виде строки, если Type System Version имеет значение SQL Server 2005. <xref:System.InvalidCastException> возникает, если данные не могут быть выражены в виде строки.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Извлекает значение указанного столбца в виде структуры <xref:System.TimeSpan>.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetValue%2A>|Извлекает указанное значение столбца в качестве базового типа CLR.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetValues%2A>|Возвращает значения столбцов в массиве.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Возвращает <xref:System.Data.DataTable>, описывающий метаданные результирующего набора.|  
  
> [!NOTE]
>  Новые `SqlDbTypes` даты и времени не поддерживаются для кода, который выполняется внутри процесса в SQL Server. Если на сервер передается один из этих типов, будет вызвано исключение.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Указание значений даты и времени в виде литералов  
Типы данных даты и времени можно указать с помощью различных форматов строковых литералов, которые SQL Server затем оцениваются во время выполнения, преобразуя их во внутренние структуры даты и времени. SQL Server распознает данные даты и времени, заключенные в одинарные кавычки ('). В следующих примерах демонстрируются некоторые форматы:  
  
- Алфавитные форматы даты, например `'October 15, 2006'`.  
  
- Числовые форматы даты, например `'10/15/2006'`.  
  
- Неразделенные строковые форматы, например `'20061015'`, которые будут интерпретироваться как 15 октября 2006, если используется формат даты в стандарте ISO.  
  
> [!NOTE]
>  Полную документацию по всем форматам строковых литералов и другим функциям типов данных даты и времени можно найти в электронная документация на SQL Server.  
  
Значения времени, которые меньше нуля или больше или равны 24 часам, вызовут <xref:System.ArgumentException>.  
  
## <a name="resources-in-sql-server-2008-books-online"></a>Материалы по SQL Server 2008 электронной документации  
Дополнительные сведения о работе со значениями даты и времени в SQL Server 2008 см. в следующих ресурсах электронной документации по SQL Server 2008.  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Типы данных и функции даты и времени (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|Приводятся общие сведения обо всех типах данных и функциях даты и времени в языке Transact-SQL.|  
|[Использование данных даты и времени](https://go.microsoft.com/fwlink/?LinkId=98361)|Приводятся сведения и даются примеры использования функций и типов данных даты и времени.|  
|[Типы данных (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98362)|Описывает системные типы данных в SQL Server 2008.|  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Типы данных SQL Server и ADO.NET](sql-server-data-types.md)
