---
title: Использование возвращающих табличные значения параметров | Документация Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3af61054-a886-4e1a-ad85-93f87c6d3584
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 99c1123ae138baf883d883731ba8749bae54ae85
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662396"
---
# <a name="using-table-valued-parameters"></a>Использование параметров, возвращающих табличные значения

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Параметры, возвращающие табличное значение, упрощают маршалинг нескольких строк данных из клиентского приложения в SQL Server, устраняя потребность в нескольких круговых путях или специальной серверной логике для обработки данных. Параметры, возвращающие табличное значение, можно использовать для инкапсуляции строк данных в клиентском приложении и их отправки на сервер единой параметризованной командой. Входящие строки данных хранятся в переменной таблицы, которая может затем можно работать с помощью Transact-SQL.  
  
Значения столбца в возвращающих табличные значения параметров может осуществляться с помощью стандартных инструкций Transact-SQL SELECT. Возвращающие табличное значение параметры строго типизированы и автоматически проверяются на их структуры. Размер для возвращающих табличные значения параметров ограничено только объемом памяти на сервере.  
  
> [!NOTE]  
> Поддержка возвращающих табличное значение параметрах доступна, начиная с Microsoft JDBC Driver 6.0 для SQL Server.
>
> Не может возвращать данные в табличное значение параметра. Табличное значение параметры являются исключительно входными. Ключевое слово OUTPUT не поддерживается.  
  
 Дополнительные сведения о возвращающих табличные значения параметров см. следующие ресурсы.  
  
| Ресурс                                                                                                             | Описание                                                                         |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| [Возвращающие табличные значения параметров (ядро СУБД)](http://go.microsoft.com/fwlink/?LinkId=98363) в электронной документации по SQL Server | Описывается создание и использование возвращающих табличные значения параметры                             |
| [Определяемые пользователем табличные типы](http://go.microsoft.com/fwlink/?LinkId=98364) в электронной документации по SQL Server                  | Описывает определяемые пользователем табличные типы, которые используются для объявления возвращающих табличное значение параметров |
| [Ядра СУБД Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=120507) раздел CodePlex        | Содержит образцы, демонстрирующие способы использования средств и функций SQL Server  |
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Передача нескольких строк в предыдущих версиях SQL Server  

Прежде чем возвращающие табличное значение параметры появились до SQL Server 2008, были ограничены возможности передачи нескольких строк данных в хранимую процедуру или параметризованную команду SQL. Разработчик может воспользоваться одним из следующих параметров для передачи нескольких строк на сервер:  
  
- Использование ряда отдельных параметров для представления значений в нескольких столбцах и строках данных. Объем данных, который может быть передан с помощью этого метода, ограничивается число разрешенных параметров. Процедуры SQL Server можно использовать максимум 2100 параметров. Логику на стороне сервера является обязательным для сборки отдельных значений в табличную переменную или временную таблицу для обработки.  
  
- Объединение нескольких значений данных в строки с разделителями или XML-документов, а затем передать этих текстовых значений в процедуру или инструкцию. Это требует процедуру или инструкцию необходимо включить логику, необходимую для проверки структур данных и разделения значений.  
  
- Создание ряда отдельных инструкций SQL для изменения данных, которые влияют на несколько строк. Изменения можно отправить на сервер по отдельности или объединенными в группы. Тем не менее даже в том случае, при отправке в пакетах из нескольких инструкций, каждая инструкция выполняется отдельно на сервере.  
  
- Использование служебной программы bcp или [SQLServerBulkCopy](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy(v=vs.110).aspx) объекта, чтобы загрузить несколько строк данных в таблицу. Несмотря на то, что этот прием очень эффективен, он не поддерживает обработку на стороне сервера, пока данные загружаются в временную таблицу или табличную переменную.  
  
## <a name="creating-table-valued-parameter-types"></a>Создание типов параметров, возвращающих табличные значения  

Возвращающие табличное значение параметры основаны на строго типизированных табличных структурах, заданных с помощью Transact-SQL `CREATE TYPE` инструкций. Необходимо создать табличный тип и определить структуру в SQL Server, перед использованием в клиентских приложениях возвращающих табличные значения параметров. Дополнительные сведения о создании типов таблиц см. в разделе [определяемые пользователем табличные типы](http://go.microsoft.com/fwlink/?LinkID=98364) в электронной документации по SQL Server.  

```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```

После создания табличного типа, можно объявить возвращающие табличные значения параметров в зависимости от конкретного типа. В следующем фрагменте языка Transact-SQL демонстрируется объявление возвращающего табличное значение параметра в определении хранимой процедуры. Обратите внимание, что `READONLY` ключевое слово является обязательным для объявления возвращающих табличные значения параметра.  

```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```

## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Изменение данных с помощью параметров, возвращающих табличные значения (Transact-SQL)  

Возвращающие табличные значения параметры могут использоваться в данных на основе набора изменений, которые влияют на несколько строк, выполнив одну инструкцию. Например можно выбрать все строки в табличное значение параметра и вставить их в таблицу базы данных, или можно создать инструкции update, соединив табличное значение параметра для таблицы, которую вы хотите обновить.  
  
Следующая инструкция Transact-SQL UPDATE демонстрируется использование возвращающих табличные значения параметра, присоединив ее в таблицу Categories. При использовании возвращающих табличные значения параметра в JOIN в предложении FROM, необходимо также псевдоним, как показано ниже, где табличное значение параметра — псевдоним «ec»:  

```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```

Этот пример Transact-SQL демонстрируется выбор строк из возвращающих табличные значения параметра для выполнения инструкции INSERT в рамках одной операции с множествами.

```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```

## <a name="limitations-of-table-valued-parameters"></a>Ограничения возвращающих табличные значения параметров

Существует несколько ограничений для возвращающих табличные значения параметров:  
  
- Возвращающие табличное значение параметры нельзя передавать до определяемых пользователем функций.  
  
- Табличное значение параметры можно индексировать только для поддержки ограничений UNIQUE или PRIMARY KEY. SQL Server не ведет статистику возвращающих табличные значения параметров.  
  
- Возвращающие табличные значения параметры являются доступными только для чтения в коде Transact-SQL. Не удается обновить значения столбцов в строках табличное значение параметра и не удается добавить или удалить строки. Для изменения данных, который передается в хранимую процедуру или параметризованную инструкцию через возвращающий табличное значение параметра, необходимо вставить данные во временную таблицу или табличную переменную.  
  
- Инструкции ALTER TABLE нельзя использовать для изменения структуры возвращающего табличное значение параметров.

- Можно осуществлять потоковую передачу больших объектов в табличное значение параметра.  
  
## <a name="configuring-a-table-valued-parameter"></a>Настройка возвращающего табличные значения параметра

Начиная с Microsoft JDBC Driver 6.0 для SQL Server, возвращающие табличные значения параметры поддерживаются параметризованную инструкцию или параметризированную хранимую процедуру. Возвращающие табличные значения параметров могут заполняться из SQLServerDataTable, из ResultSet или из пользователя при условии реализации интерфейса ISQLServerDataRecord. При задании табличное значение параметра для подготовленного запроса, необходимо указать имя типа, который должен совпадать с именем совместимого типа, созданного ранее на сервере.  
  
Следующие два фрагмента кода показано, как настроить табличное значение параметра с SQLServerPreparedStatement и SQLServerCallableStatement для вставки данных. Здесь sourceTVPObject может быть SQLServerDataTable, ResultSet или объект ISQLServerDataRecord. В примерах предполагается, что подключение является активным объектом соединения.  

```java
// Using table-valued parameter with a SQLServerPreparedStatement.  
SQLServerPreparedStatement pStmt =
    (SQLServerPreparedStatement) connection.prepareStatement(“INSERT INTO dbo.Categories SELECT * FROM ?”);  
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
> См. в разделе **возвращающего табличное значение параметра API для драйвера JDBC** ниже полный список интерфейсов API, позволяющих задать для возвращающих табличные значения параметра.  
  
## <a name="passing-a-table-valued-parameter-as-a-sqlserverdatatable-object"></a>Передача табличное значение параметра как объект SQLServerDataTable  

Начиная с Microsoft JDBC Driver 6.0 для SQL Server, класс SQLServerDataTable представляет таблицу в памяти реляционных данных. В этом примере демонстрируется создание возвращающих табличные значения параметра из данных в памяти, с помощью объекта SQLServerDataTable. Код сначала создает объект SQLServerDataTable, определяет его схемы и заполняет таблицу данных. Затем в коде настраивается SQLServerPreparedStatement, который передает этой таблицы данных как табличное значение параметра в SQL Server.  

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
> См. в разделе **возвращающего табличное значение параметра API для драйвера JDBC** ниже полный список интерфейсов API, позволяющих задать для возвращающих табличные значения параметра.  
  
## <a name="passing-a-table-valued-parameter-as-a-resultset-object"></a>Передача табличное значение параметра как объект результирующего набора  

В этом примере показано, как выполнять потоковую передачу строк данных из результирующего набора для возвращающих табличные значения параметра. Код сначала получает данные из исходной таблицы в создает объект SQLServerDataTable, определяет его схемы и заполняет таблицу данных. Затем в коде настраивается SQLServerPreparedStatement, который передает этой таблицы данных как табличное значение параметра в SQL Server.  

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
> См. в разделе **возвращающего табличное значение параметра API для драйвера JDBC** ниже полный список интерфейсов API, позволяющих задать для возвращающих табличные значения параметра.  

## <a name="passing-a-table-valued-parameter-as-an-isqlserverdatarecord-object"></a>Передача табличное значение параметра как объект ISQLServerDataRecord  

Начиная с Microsoft JDBC Driver 6.0 для SQL Server, новый интерфейс ISQLServerDataRecord доступен для потоковой передачи данных (в зависимости от как пользователь предоставляет реализацию для него) с помощью возвращающих табличные значения параметра. В следующем примере для реализации интерфейса ISQLServerDataRecord и передайте его в качестве параметров, возвращающих табличные значения. Для простоты в следующем примере передается только одну строку с жестко заданные значения для возвращающих табличные значения параметра. В идеале пользователю будет реализовывать этот интерфейс для передачи строк из любого источника, например из текстовых файлов.  

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
> См. в разделе **возвращающего табличное значение параметра API для драйвера JDBC** ниже полный список интерфейсов API, позволяющих задать для возвращающих табличные значения параметра.

## <a name="table-valued-parameter-api-for-the-jdbc-driver"></a>Табличное значение параметра API для драйвера JDBC

### <a name="sqlservermetadata"></a>SQLServerMetaData

Этот класс представляет метаданные для столбца. Он используется в интерфейсе ISQLServerDataRecord для передачи метаданных столбцов возвращающих табличные значения параметра. Методы этого класса являются:  

| Имя                                                                                                                                                                             | Описание                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| открытый SQLServerMetaData (columnName строки, int sqlType, int точности, масштаба int, логическое useServerDefault, логическое isUniqueKey, SQLServerSortOrder sortOrder, int sortOrdinal) | Инициализирует новый экземпляр SQLServerMetaData с заданных значений имени столбца, тип sql, точность, масштаб и сервера по умолчанию. Эта форма конструктора поддерживает параметры, возвращающие табличные значения, позволяя указать, уникален ли столбец в параметре с табличным значением, порядок сортировки столбца и порядковый номер столбца сортировки. <br/><br/>useServerDefault - указывает, если этот столбец должен использовать значение сервера по умолчанию; Значение по умолчанию — false.<br>isUniqueKey - указывает, уникален ли столбец в параметре с табличным; Значение по умолчанию — false.<br>sortOrder - указывает порядок сортировки для столбца; Значение по умолчанию — SQLServerSortOrder.Unspecified.<br>sortOrdinal - указывает порядковый номер столбца сортировки; sortOrdinal начинается с 0; Значение по умолчанию равно -1. |
| открытый SQLServerMetaData (columnName строки, int sqlType)                                                                                                                        | Инициализирует новый экземпляр класса SQLServerMetaData, используя имя столбца и тип sql.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| открытый SQLServerMetaData (columnName строки, int sqlType, int точности и масштаба int)                                                                                              | Инициализирует новый экземпляр класса SQLServerMetaData, используя имя столбца, тип sql, точность и масштаб.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Открытый SQLServerMetaData (SQLServerMetaData sqlServerMetaData)                                                                                                                    | Инициализирует новый экземпляр класса SQLServerMetaData выполняется из другого объекта SQLServerMetaData.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| открытый getColumName() строки                                                                                                                                                     | Получает имя столбца.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| открытый int getSqlType()                                                                                                                                                          | Извлекает тип sql java.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| открытый int getPrecision()                                                                                                                                                        | Возвращает точность типа, передаваемый в столбце.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| открытый int getScale()                                                                                                                                                            | Возвращает масштаб типа, передаваемый в столбце.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| открытый getSortOrder() SQLServerSortOrder                                                                                                                                         | Получает порядок сортировки.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| открытый int getSortOrdinal()                                                                                                                                                      | Извлекает порядковый номер сортировки.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| открытый логическое isUniqueKey()                                                                                                                                                     | Указывает, является ли столбец уникальным.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| открытый логическое useServerDefault()                                                                                                                                                | Осуществляет ли возвращает столбец использует значение сервера по умолчанию.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
  
### <a name="sqlserversortorder"></a>SQLServerSortOrder

Перечисление, которое определяет порядок сортировки. Возможные значения: по возрастанию, по убыванию и не указано.
  
### <a name="sqlserverdatatable"></a>SQLServerDataTable

Этот класс представляет таблицу данных в памяти для использования с возвращающих табличные значения параметров. Методы этого класса являются:  

| Имя                                                          | Описание                                          |
| ------------------------------------------------------------- | ---------------------------------------------------- |
| Открытый SQLServerDataTable()                                   | Инициализирует новый экземпляр класса SQLServerDataTable.    |
| открытый итератор < запись\<целое число, Object [] >> getIterator()      | Извлекает итератор для строк таблицы данных. |
| открытый void addColumnMetadata (columnName строки, int sqlType) | Добавляет метаданные для указанного столбца.              |
| открытый void addColumnMetadata (SQLServerDataColumn столбец)     | Добавляет метаданные для указанного столбца.              |
| открытый addRow void (значений объектов...)                          | Добавляет одну строку данных в таблицу данных.              |
| открытый карты\<целое число, SQLServerDataColumn > getColumnMetadata() | Извлекает метаданные столбца этой таблицы данных.       |
| открытый clear() void                                           | Очищает этой таблицы данных.                              |

### <a name="sqlserverdatacolumn"></a>SQLServerDataColumn

Этот класс представляет столбец в таблице данных в памяти, представленный SQLServerDataTable. Методы этого класса являются:  

| Имя                                                       | Описание                                                                      |
| ---------------------------------------------------------- | -------------------------------------------------------------------------------- |
| открытый SQLServerDataColumn (columnName строки, int sqlType) | Инициализирует новый экземпляр SQLServerDataColumn с именем столбца и типом. |
| открытый getColumnName() строки                              | Получает имя столбца.                                                       |
| открытый int getColumnType()                                 | Извлекает тип столбца.                                                       |

### <a name="isqlserverdatarecord"></a>ISQLServerDataRecord

Этот класс представляет интерфейс, который пользователи могут реализовать для потоковой передачи данных для возвращающих табличные значения параметра. Методы в этом интерфейсе являются:  
  
| Имя                                                    | Описание                                                                                             |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| открытый SQLServerMetaData getColumnMetaData (столбца данных типа int); | Извлекает метаданные столбца индекса заданного столбца.                                               |
| открытый int getColumnCount();                            | Возвращает общее число столбцов.                                                                  |
| открытый getRowData() объекта [];                           | Получает данные для текущей строки как массив объектов.                                          |
| открытый логическое next();                                  | Переходит к следующей строке. Возвращает значение True, если перемещение выполнено успешно, а следующую строку, и false в противном случае. |

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

Следующие методы были добавлены к этому классу для поддержки передачи таких параметров, возвращающих табличные значения.  

| Имя                                                                                                    | Описание                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| открытый окончательный void setStructured (int parameterIndex, строка tvpName, SQLServerDataTable tvpDataTbale)    | Заполняет возвращающие табличное значение параметра с таблицей данных. parameterIndex является индексом параметра, tvpName — это имя табличное значение параметра и tvpDataTable является исходный объект таблицы данных.                                                                                                          |
| открытый окончательный void setStructured (int parameterIndex, tvpName строку, tvpResultSet результирующий набор)             | Возвращающие табличное значение параметра заполняет набор результатов, полученных из другой таблицы. parameterIndex является индекс параметра, tvpName — это имя табличное значение параметра и tvpResultSet является исходный объект результирующего набора.                                                                               |
| открытый окончательный void setStructured (int parameterIndex, строка tvpName, ISQLServerDataRecord tvpDataRecord) | Заполняет возвращающие табличное значение параметр с объектом ISQLServerDataRecord. ISQLServerDataRecord используется для потоковой передачи данных и пользователь решает способы его использования. parameterIndex по индексу параметра, tvpName является имя параметра с табличным, которое tvpDataRecord объект ISQLServerDataRecord. |
  
### <a name="sqlservercallablestatement"></a>SQLServerCallableStatement

Следующие методы были добавлены к этому классу для поддержки передачи таких параметров, возвращающих табличные значения.  
  
| Имя                                                                                                        | Описание                                                                                                                                                                                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| открытый окончательный void setStructured (paratemeterName строка, строка tvpName, SQLServerDataTable tvpDataTable)    | Заполняет возвращающие табличное значение параметра, передаваемое в хранимую процедуру с таблицу данных. paratemeterName — это имя параметра, tvpName — это имя типа возвращающего табличное значение Параметра и tvpDataTable — это объект таблицы данных.                                                                                                                 |
| открытый окончательный void setStructured (paratemeterName строка, строка tvpName, tvpResultSet результирующий набор)             | Заполняет возвращающие табличное значение параметра, передаваемого хранимой процедуры с набором результатов, полученных из другой таблицы. paratemeterName — это имя параметра и tvpName — это имя типа возвращающего табличное значение Параметра tvpResultSet является исходный объект результирующего набора.                                                                              |
| открытый окончательный void setStructured (paratemeterName строка, строка tvpName, ISQLServerDataRecord tvpDataRecord) | Заполняет возвращающие табличное значение параметра, передаваемого хранимой процедуры с объектом ISQLServerDataRecord. ISQLServerDataRecord используется для потоковой передачи данных и пользователь решает способы его использования. paratemeterName — это имя параметра, tvpName — это имя типа возвращающего табличное значение Параметра и tvpDataRecord — это объект ISQLServerDataRecord. |

## <a name="see-also"></a>См. также:

[Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
