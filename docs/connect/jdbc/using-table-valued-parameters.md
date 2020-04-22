---
title: Использование параметров, возвращающих табличные значения
description: Возвращающие табличные значения параметры обеспечивают эффективный способ отправки нескольких строк данных от клиента к SQL Server в одной параметризованной команде.
ms.custom: ''
ms.date: 11/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3af61054-a886-4e1a-ad85-93f87c6d3584
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 698cf6e4e44210ea5f4575d4021514c07fe4255d
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81631944"
---
# <a name="using-table-valued-parameters"></a>Использование параметров, возвращающих табличные значения

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Параметры, возвращающие табличное значение, упрощают маршалинг нескольких строк данных из клиентского приложения в SQL Server, устраняя потребность в нескольких круговых путях или специальной серверной логике для обработки данных. Параметры, возвращающие табличное значение, можно использовать для инкапсуляции строк данных в клиентском приложении и их отправки на сервер единой параметризованной командой. Входящие строки данных хранятся в переменной таблицы, которой затем можно управлять с помощью Transact-SQL.  
  
Доступ к значениям столбца в возвращающих табличное значение параметрах обеспечивается с помощью стандартных инструкций Transact-SQL SELECT. Возвращающие табличное значение параметры строго типизированы, и проверка их структуры происходит автоматически. Размер возвращающих табличное значение параметров ограничен только объемом памяти сервера.  
  
> [!NOTE]  
> Поддержка возвращающих табличное значение параметров доступна, начиная с Microsoft JDBC Driver 6.0 для SQL Server.
>
> В параметре, возвращающем табличное значение, невозможно вернуть данные. Возвращающие табличное значение параметры являются только входными. Ключевое слово OUTPUT не поддерживается.  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в следующих ресурсах.  
  
| Ресурс                                                                                                             | Описание                                                                         |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| [Возвращающие табличное значение параметры (ядро СУБД)](https://go.microsoft.com/fwlink/?LinkId=98363) в электронной документации на SQL Server | Здесь описывается создание и использование возвращающих табличное значение параметров.                             |
| [Определяемые пользователем табличные типы](https://go.microsoft.com/fwlink/?LinkId=98364) в электронной документации на SQL Server                  | Здесь описывается использование определяемых пользователем табличных типов для объявления возвращающих табличное значение параметров. |
| Раздел [Ядро СУБД Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=120507) веб-узла CodePlex        | Здесь содержатся образцы, в которых демонстрируется использование возможностей и функций SQL Server.  |
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Передача нескольких строк в предыдущих версиях SQL Server  

До появления в SQL Server 2008 параметров, возвращающих табличное значение, были ограниченны возможности передачи нескольких строк данных в хранимую процедуру или параметризованную команду SQL. Разработчик может выбрать один из следующих вариантов передачи нескольких строк на сервер.  
  
- Использовать ряд отдельных параметров, чтобы представить значения в нескольких столбцах и строках данных. Объем данных, которые можно передать с помощью этого метода, ограничен количеством допустимых параметров. В процедурах SQL Server можно использовать не более 2100 параметров. Для сборки этих отдельных значений в табличную переменную или временную таблицу для обработки требуется логика на стороне сервера.  
  
- Объединить несколько значений данных в строки с разделителями или документы XML, а затем передать эти текстовые значения в процедуру или инструкцию. Для этого требуется, чтобы процедура или инструкция содержали логику, необходимую для проверки структур данных и разъединения значений.  
  
- Создать ряд отдельных инструкций SQL для изменений данных, затрагивающих несколько строк. Изменения можно отправлять на сервер по отдельности или объединять в группы. Тем не менее даже при отправке в пакетах, содержащих несколько инструкций, каждая из них выполняется на сервере отдельно.  
  
- Использовать программу bcp или [SQLServerBulkCopy](using-bulk-copy-with-the-jdbc-driver.md), чтобы загрузить в таблицу множество строк данных. Хотя этот метод очень эффективен, он не поддерживает обработку на стороне сервера, если данные не загружены во временную таблицу или табличную переменную.
  
## <a name="creating-table-valued-parameter-types"></a>Создание типов параметров, возвращающих табличное значение  

Возвращающие табличное значение параметры основаны на строго типизированных табличных структурах, заданных с помощью инструкций Transact-SQL `CREATE TYPE`. Перед использованием в клиентских приложениях возвращающих табличное значение параметров в SQL Server необходимо создать табличный тип и определить структуру. Дополнительные сведения о создании типов таблиц см. в разделе [Определяемые пользователем табличные типы](https://go.microsoft.com/fwlink/?LinkID=98364) электронной документации на SQL Server.  

```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```

После создания табличного типа можно объявить возвращающие табличное значение параметры на основе этого типа. В приведенном ниже фрагменте кода Transact-SQL демонстрируется объявление возвращающего табличное значение параметра в определении хранимой процедуры. Обратите внимание, что для объявления возвращающего табличное значение параметра требуется ключевое слово `READONLY`.  

```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```

## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Изменение данных с помощью возвращающих табличное значение параметров (Transact-SQL)  

Возвращающие табличное значение параметры можно использовать во влияющих на несколько строк изменениях данных на основе наборов, выполняя одну инструкцию. Например, можно выбрать в возвращающем табличное значение параметре все строки и вставить их в таблицу базы данных. Кроме того, можно создать инструкцию UPDATE, присоединив возвращающий табличное значение параметр к таблице, которую необходимо обновить.  
  
В приведенной ниже инструкции Transact-SQL UPDATE демонстрируется соединение возвращающего табличное значение параметра с таблицей Categories. При использовании возвращающего табличное значение параметра со значением JOIN в предложении FROM необходимо также присвоить ему псевдоним, как показано здесь, где параметр с табличным значением имеет псевдоним "ec":  

```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```

В этом примере кода Transact-SQL демонстрируется выбор строк из возвращающего табличное значение параметра для выполнения инструкции INSERT в одной операции на основе набора данных.

```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```

## <a name="limitations-of-table-valued-parameters"></a>Ограничения возвращающих табличное значение параметров

Для возвращающих табличное значение параметров существует несколько ограничений.  
  
- Возвращающие табличное значение параметры нельзя передавать определяемым пользователем функциям.  
  
- Возвращающие табличное значение параметры могут индексироваться только для поддержки ограничений UNIQUE или PRIMARY KEY. SQL Server не ведет статистику возвращающих табличные значения параметров.  
  
- В коде Transact-SQL возвращающие табличное значение параметры предназначены только для чтения. Нельзя обновлять значения столбцов в строках возвращающего табличное значение параметра, а также вставлять или удалять строки. Чтобы изменить данные, передаваемые в хранимую процедуру или параметризованную инструкцию в возвращающем табличное значение параметре, необходимо вставить данные во временную таблицу или в табличную переменную.  
  
- Нельзя использовать инструкции ALTER TABLE для изменения структуры возвращающих табличное значение параметров.

- В возвращающем табличное значение параметре можно передавать большие объекты.  
  
## <a name="configuring-a-table-valued-parameter"></a>Настройка параметра, возвращающего табличные значения

Начиная с Microsoft JDBC Driver 6.0 для SQL Server, возвращающие табличное значение параметры поддерживаются с параметризованной инструкцией или параметризованной хранимой процедурой. Возвращающие табличное значение параметры можно заполнить из таблицы SQLServerDataTable, из результирующего набора или из реализации интерфейса ISQLServerDataRecord, предоставленного пользователем. При указании возвращающего табличное значение параметра для подготовленного запроса необходимо указать имя типа, которое должно совпадать с именем совместимого типа, ранее созданного на сервере.  
  
В следующих двух фрагментах кода показано, как настроить возвращающий табличное значение параметр с инструкциями SQLServerPreparedStatement и SQLServerCallableStatement для вставки данных. Здесь объект sourceTVPObject может быть объектом SQLServerDataTable, результирующим набором или объектом ISQLServerDataRecord. В примерах предполагается, что подключение является активным объектом Connection.  

```java
// Using table-valued parameter with a SQLServerPreparedStatement.  
SQLServerPreparedStatement pStmt =
    (SQLServerPreparedStatement) connection.prepareStatement("INSERT INTO dbo.Categories SELECT * FROM ?");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);  
pStmt.execute();  
```

```java
// Using table-valued parameter with a SQLServerCallableStatement.  
SQLServerCallableStatement pStmt =
    (SQLServerCallableStatement) connection.prepareCall("exec usp_InsertCategories ?");
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);;  
pStmt.execute();  
```

> [!NOTE]  
> Полный список интерфейсов API, доступных для настройки возвращающего табличное значение параметра, см. в разделе **API-интерфейс возвращающего табличное значение параметра для драйвера JDBC** ниже.  
  
## <a name="passing-a-table-valued-parameter-as-a-sqlserverdatatable-object"></a>Передача возвращающего табличное значение параметра в виде объекта SQLServerDataTable  

Начиная с Microsoft JDBC Driver 6.0 для SQL Server, класс SQLServerDataTable представляет таблицу реляционных данных в памяти. В этом примере показано, как создать возвращающий табличное значение параметр из данных в памяти с помощью объекта SQLServerDataTable. Сначала код создает объект SQLServerDataTable, определяет его схему и заполняет таблицу данными. Затем код настраивает SQLServerPreparedStatement, который передает эту таблицу данных в качестве возвращающего табличное значение параметра для SQL Server.  

```java
/* Assumes connection is an active Connection object. */

// Create an in-memory data table.  
SQLServerDataTable sourceDataTable = new SQLServerDataTable();
  
// Define metadata for the data table.  
sourceDataTable.addColumnMetadata("CategoryID" ,java.sql.Types.INTEGER);
sourceDataTable.addColumnMetadata("CategoryName" ,java.sql.Types.NVARCHAR);
  
// Populate the data table.  
sourceDataTable.addRow(1, "CategoryNameValue1");
sourceDataTable.addRow(2, "CategoryNameValue2");
  
// Pass the data table as a table-valued parameter using a prepared statement.  
SQLServerPreparedStatement pStmt =
        (SQLServerPreparedStatement) connection.prepareStatement(  
            "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceDataTable);  
pStmt.execute();  
```

> [!NOTE]  
> Полный список интерфейсов API, доступных для настройки возвращающего табличное значение параметра, см. в разделе **API-интерфейс возвращающего табличное значение параметра для драйвера JDBC** ниже.  
  
## <a name="passing-a-table-valued-parameter-as-a-resultset-object"></a>Передача возвращающего табличное значение параметра в виде объекта ResultSet  

В этом примере демонстрируется потоковая передача строк данных из результирующего набора в возвращающий табличное значение параметр. Сначала код извлекает данные из исходной таблицы, создает объект SQLServerDataTable, определяет его схему и заполняет таблицу данными. Затем код настраивает SQLServerPreparedStatement, который передает эту таблицу данных в качестве возвращающего табличное значение параметра для SQL Server.  

```java
/* Assumes connection is an active Connection object. */

// Create the source ResultSet object. Here SourceCategories is a table defined with the same schema as Categories table.
ResultSet sourceResultSet = connection.createStatement().executeQuery("SELECT * FROM SourceCategories");  

// Pass the source result set as a table-valued parameter using a prepared statement.  
SQLServerPreparedStatement pStmt =
        (SQLServerPreparedStatement) connection.prepareStatement(  
                "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceResultSet);  
pStmt.execute();  
```

> [!NOTE]  
> Полный список интерфейсов API, доступных для настройки возвращающего табличное значение параметра, см. в разделе **API-интерфейс возвращающего табличное значение параметра для драйвера JDBC** ниже.  

## <a name="passing-a-table-valued-parameter-as-an-isqlserverdatarecord-object"></a>Передача возвращающего табличное значение параметра в виде объекта ISQLServerDataRecord  

Начиная с Microsoft JDBC Driver 6.0 для SQL Server, доступен новый интерфейс ISQLServerDataRecord для потоковой передачи данных (в зависимости от того, как пользователь предоставляет реализацию) с помощью возвращающего табличное значение параметра. В следующем примере показано, как реализовать интерфейс ISQLServerDataRecord и передать его в качестве возвращающего табличное значение параметра. Для простоты в следующем примере в возвращающий табличное значение параметр передается только одна строка с жестко заданными значениями. В идеале пользователь будет реализовывать этот интерфейс для потоковой передачи строк из любого источника, например из текстовых файлов.  

```java
class MyRecords implements ISQLServerDataRecord  
{  
    int currentRow = 0;  
    Object[] row = new Object[2];  
  
    MyRecords(){  
        // Constructor. This implementation has just one row.
        row[0] = new Integer(1);  
        row[1] = "categoryName1";  
    }  
  
    public int getColumnCount(){  
        // Return the total number of columns, for this example it is 2.  
        return 2;  
    }  
  
    public SQLServerMetaData getColumnMetaData(int columnIndex) {  
        // Return the column metadata.  
        if (1 == columnIndex)  
            return new SQLServerMetaData("CategoryID", java.sql.Types.INTEGER);  
        else  
            return new SQLServerMetaData("CategoryName", java.sql.Types.NVARCHAR);  
    }  
  
    public Object[] getRowData(){  
        // Return the columns in the current row as an array of objects. This implementation has just one row.  
        return row;
    }  
  
    public boolean next(){  
        // Move to the next row. This implementation has just one row, after processing the first row, return false.  
        currentRow++;  
        if (1 == currentRow)  
            return true;  
        else  
            return false;  
    }
}

// Following code demonstrates how to pass MyRecords object as a table-valued parameter.  
MyRecords sourceRecords = new MyRecords();  
SQLServerPreparedStatement pStmt =
        (SQLServerPreparedStatement) connection.prepareStatement(  
                "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceRecords);  
pStmt.execute();  
```

> [!NOTE]  
> Полный список интерфейсов API, доступных для настройки возвращающего табличное значение параметра, см. в разделе **API-интерфейс возвращающего табличное значение параметра для драйвера JDBC** ниже.

## <a name="table-valued-parameter-api-for-the-jdbc-driver"></a>API-интерфейс возвращающего табличное значение параметра для драйвера JDBC

### <a name="sqlservermetadata"></a>SQLServerMetaData

Этот класс представляет метаданные для столбца. Он используется в интерфейсе ISQLServerDataRecord для передачи метаданных столбца в возвращающий табличное значение параметр. В этом классе используются следующие методы.  

| Имя                                                                                                                                                                             | Описание                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| public SQLServerMetaData(String columnName, int sqlType, int precision, int scale, boolean useServerDefault, boolean isUniqueKey, SQLServerSortOrder sortOrder, int sortOrdinal) | Инициализирует новый экземпляр SQLServerMetaData с указанным именем столбца, типом SQL, точностью, масштабом и сервером по умолчанию. Эта форма конструктора поддерживает возвращающие табличное значение параметры, позволяя указать, является ли столбец в таком параметре уникальным, а также порядок сортировки столбца и порядковый номер столбца сортировки. <br/><br/>Объект useServerDefault — указывает, должно ли в этом столбце использоваться значение сервера по умолчанию. Значение по умолчанию — false.<br>Объект isUniqueKey — указывает, является ли столбец в возвращающем табличное значение параметре уникальным. Значение по умолчанию — false.<br>Объект sortOrder — указывает порядок сортировки для столбца. Значение по умолчанию — QLServerSortOrder.Unspecified.<br>Объект sortOrdinal — указывает порядковый номер столбца сортировки. Значения sortOrdinal начинаются с 0. Значение по умолчанию: −1. |
| public SQLServerMetaData( String columnName, int sqlType)                                                                                                                        | Инициализирует новый экземпляр SQLServerMetaData, используя имя столбца и тип SQL.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| public SQLServerMetaData( String columnName, int sqlType, int length)                                                                                                                        | Инициализирует новый экземпляр SQLServerMetaData, используя имя столбца, тип SQL и длину (для строковых данных). Длина используется для различения больших строк и строк длиной менее 4000 символов. Этот метод представлен в версии 7.2 драйвера JDBC.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| public SQLServerMetaData( String columnName, int sqlType, int precision, int scale)                                                                                              | Инициализирует новый экземпляр SQLServerMetaData, используя имя столбца, тип SQL, точность и масштаб.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Public SQLServerMetaData(SQLServerMetaData sqlServerMetaData)                                                                                                                    | Инициализирует новый экземпляр класса SQLServerMetaData из другого объекта SQLServerMetaData.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| public String getColumName()                                                                                                                                                     | Извлекает имя столбца.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| public int getSqlType()                                                                                                                                                          | Извлекает тип Java SQL.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| public int getPrecision()                                                                                                                                                        | Извлекает точность типа, переданного в столбец.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| public int getScale()                                                                                                                                                            | Извлекает масштаб типа, переданного в столбец.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| public SQLServerSortOrder getSortOrder()                                                                                                                                         | Извлекает порядок сортировки.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| public int getSortOrdinal()                                                                                                                                                      | Извлекает порядковый номер сортировки.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| public boolean isUniqueKey()                                                                                                                                                     | Извлекает значение, указывающее, является ли столбец уникальным.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| public boolean useServerDefault()                                                                                                                                                | Возвращает значение, указывающее, использует ли столбец значение сервера по умолчанию.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
  
### <a name="sqlserversortorder"></a>SQLServerSortOrder

Перечисление, определяющее порядок сортировки. Допустимые значения: Ascending, Descending и Unspecified.
  
### <a name="sqlserverdatatable"></a>SQLServerDataTable

Этот класс представляет таблицу данных в памяти для использования с возвращающими табличное значение параметрами. В этом классе используются следующие методы.  

| Имя                                                          | Описание                                          |
| ------------------------------------------------------------- | ---------------------------------------------------- |
| Public SQLServerDataTable()                                   | Инициализирует новый экземпляр SQLServerDataTable.    |
| public Iterator<Entry\<Integer, Object[]>> getIterator()      | Извлекает итератор в строках таблицы данных. |
| public void addColumnMetadata(String columnName, int sqlType) | Добавляет метаданные для указанного столбца.              |
| public void addColumnMetadata(SQLServerDataColumn column)     | Добавляет метаданные для указанного столбца.              |
| public void addRow(Object... values)                          | Добавляет одну строку данных в таблицу данных.              |
| public Map\<Integer, SQLServerDataColumn> getColumnMetadata() | Извлекает метаданные столбца этой таблицы данных.       |
| public void clear()                                           | Очищает эту таблицу данных.                              |

### <a name="sqlserverdatacolumn"></a>SQLServerDataColumn

Этот класс представляет столбец таблицы данных в памяти, представленный SQLServerDataTable. В этом классе используются следующие методы.  

| Имя                                                       | Описание                                                                      |
| ---------------------------------------------------------- | -------------------------------------------------------------------------------- |
| public SQLServerDataColumn(String columnName, int sqlType) | Инициализирует новый экземпляр SQLServerDataColumn с именем и типом столбца. |
| public String getColumnName()                              | Извлекает имя столбца.                                                       |
| public int getColumnType()                                 | Извлекает тип столбца.                                                       |

### <a name="isqlserverdatarecord"></a>ISQLServerDataRecord

Этот класс представляет интерфейс, который пользователи могут реализовать для потоковой передачи данных в возвращающий табличное значение параметр. В этом интерфейсе используются следующие методы.  
  
| Имя                                                    | Описание                                                                                             |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| public SQLServerMetaData getColumnMetaData(int column); | Извлекает метаданные столбца заданного индекса столбца.                                               |
| public int getColumnCount();                            | Извлекает общее число столбцов.                                                                  |
| public Object[] getRowData();                           | Получает данные для текущей строки как массив объектов.                                          |
| public boolean next();                                  | Переходит к следующей строке. Возвращает значение true, если перемещение выполнено успешно и имеется следующая строка. В противном случае возвращает значение false. |

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

Для поддержки передачи возвращающих табличное значение параметров в этот класс были добавлены следующие методы.  

| Имя                                                                                                    | Описание                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| public final void setStructured(int parameterIndex, String tvpName, SQLServerDataTable tvpDataTable)    | Заполняет возвращающий табличное значение параметр таблицей данных. parameterIndex — индекс параметра, tvpName — имя возвращающего табличное значение параметра, а tvpDataTable — объект исходной таблицы данных.                                                                                                          |
| public final void setStructured(int parameterIndex, String tvpName, ResultSet tvpResultSet)             | Заполняет возвращающий табличное значение параметр объектом ResultSet, полученным из другой таблицы. parameterIndex — индекс параметра, tvpName — имя возвращающего табличное значение параметра, а tvpResultSet — объект исходного результирующего набора.                                                                               |
| public final void setStructured(int parameterIndex, String tvpName, ISQLServerDataRecord tvpDataRecord) | Заполняет возвращающий табличное значение параметр объектом ISQLServerDataRecord. ISQLServerDataRecord используется для потоковой передачи данных, а пользователь решает, как его использовать. parameterIndex — индекс параметра, tvpName — имя возвращающего табличное значение параметра, а tvpDataRecord — объект ISQLServerDataRecord. |
  
### <a name="sqlservercallablestatement"></a>SQLServerCallableStatement

Для поддержки передачи возвращающих табличное значение параметров в этот класс были добавлены следующие методы.  
  
| Имя                                                                                                        | Описание                                                                                                                                                                                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| public final void setStructured(String paratemeterName, String tvpName, SQLServerDataTable tvpDataTable)    | Заполняет возвращающий табличное значение параметр, передаваемый хранимой процедуре, таблицей данных. paratemeterName — имя параметра, tvpName — имя типа TVP, а tvpDataTable — объект таблицы данных.                                                                                                                 |
| public final void setStructured(String paratemeterName, String tvpName, ResultSet tvpResultSet)             | Заполняет возвращающий табличное значение параметр, передаваемый хранимой процедуре, результирующим набором, полученным из другой таблицы. paratemeterName — имя параметра, tvpName — имя типа TVP, а tvpResultSet — исходный объект результирующего набора.                                                                              |
| public final void setStructured(String paratemeterName, String tvpName, ISQLServerDataRecord tvpDataRecord) | Заполняет возвращающий табличное значение параметр, передаваемый хранимой процедуре, объектом ISQLServerDataRecord. ISQLServerDataRecord используется для потоковой передачи данных, а пользователь решает, как его использовать. paratemeterName — имя параметра, tvpName — имя типа TVP, а ISQLServerDataRecord — объект ISQLServerDataRecord. |

## <a name="see-also"></a>См. также раздел

[Общие сведения о JDBC Driver](overview-of-the-jdbc-driver.md)  
