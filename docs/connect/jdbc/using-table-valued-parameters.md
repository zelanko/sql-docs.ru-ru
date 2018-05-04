---
title: Использование возвращающих табличные значения параметров | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3af61054-a886-4e1a-ad85-93f87c6d3584
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c6ac7155299100c0faecae67c8d8465a11305e26
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-table-valued-parameters"></a>Использование возвращающих табличные значения параметров
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Возвращающие табличное значение параметры обеспечивают простой способ упаковки строк данных из клиентского приложения к серверу SQL Server без необходимости несколько циклов приема-передачи или специальной логики на стороне сервера для обработки данных. Возвращающие табличные значения параметров можно использовать для инкапсуляции строк данных в клиентском приложении и отправки данных на сервер в одной параметризированной команды. Входящие строки данных хранятся в переменной таблицы, которое можно затем работать с помощью Transact-SQL.  
  
 Значения столбца в возвращающих табличные значения параметров осуществляется с помощью стандартных инструкций Transact-SQL SELECT. Возвращающие табличное значение параметры строго типизированы и структуры их автоматически проверить. Размер для возвращающих табличные значения параметров, ограничен только объемом памяти на сервере.  
  
> [!NOTE]  
>  Поддержка для возвращающего табличное значение параметров доступна, начиная с Microsoft JDBC Driver 6.0 для SQL Server.  
  
> [!NOTE]  
>  Не может возвращать данные в табличное значение параметра. Возвращающие табличные значения параметры являются исключительно входными. Ключевое слово OUTPUT не поддерживается.  
  
 Дополнительные сведения о возвращающих табличные значения параметров см. следующие ресурсы.  
  
|Ресурс|Описание|  
|--------------|-----------------|  
|[Возвращающие табличные значения параметров (компонент Database Engine)](http://go.microsoft.com/fwlink/?LinkId=98363) в электронной документации по SQL Server|Описывает создание и использование возвращающих табличные значения параметров|  
|[Определяемые пользователем табличные типы](http://go.microsoft.com/fwlink/?LinkId=98364) в электронной документации по SQL Server|Описывает определяемые пользователем табличные типы, которые используются для объявления возвращающих табличные значения параметров|  
|[Microsoft SQL Server Database Engine](http://go.microsoft.com/fwlink/?LinkId=120507) раздел CodePlex|Содержит образцы, демонстрирующие способы использования средств и функций SQL Server|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Передача нескольких строк в предыдущих версиях SQL Server  
 Прежде чем возвращающего табличное значение параметры появились до SQL Server 2008, были ограничены возможности передачи нескольких строк данных в хранимую процедуру или параметризованную команду SQL. Разработчик может воспользоваться одним из следующих параметров для передачи нескольких строк на сервер:  
  
-   Использование ряда отдельных параметров для представления значений в нескольких столбцах и строках данных. Объем данных, который может быть передан с помощью этого метода, ограничено число разрешенных параметров. Процедуры SQL Server может иметь, не более 2100 параметров. Для сборки отдельных значений в табличную переменную или временную таблицу для обработки требуется логику на стороне сервера.  
  
-   Объединение нескольких значений данных в строки с разделителями или XML-документов, а затем передать этих текстовых значений в процедуру или инструкцию. Это требует процедуру или инструкцию необходимо включить логику, необходимую для проверки структур данных и разделения значений.  
  
-   Создайте несколько отдельных инструкций SQL для изменения данных, которые влияют на несколько строк. Изменения можно отправить на сервер по отдельности или объединенными в группы. Тем не менее даже при отправке в пакетах из нескольких инструкций, каждая инструкция выполняется отдельно на сервере.  
  
-   Использование служебной программы bcp или [SQLServerBulkCopy](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy(v=vs.110).aspx) объекта, чтобы загрузить несколько строк данных в таблицу. Хотя этот метод очень эффективен, он не поддерживает серверные обработки, если данные загружаются в временную таблицу или табличную переменную.  
  
## <a name="creating-table-valued-parameter-types"></a>Создание типов параметров, возвращающих табличные значения  
 Возвращающие табличные значения параметры основаны на строго типизированных табличных структурах, заданных с помощью инструкций Transact-SQL CREATE TYPE. Необходимо создать тип таблицы и определить структуру в SQL Server, перед использованием в клиентских приложениях возвращающих табличные значения параметров. Дополнительные сведения о создании типов таблиц см. в разделе [определяемые пользователем табличные типы](http://go.microsoft.com/fwlink/?LinkID=98364) в электронной документации по SQL Server.  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 После создания табличного типа, можно объявить возвращающие табличные значения параметры, основанные на этом типе. В следующем фрагменте языка Transact-SQL демонстрирует объявления возвращающих табличные значения параметра в определении хранимой процедуры. Обратите внимание, что ключевое слово READONLY необходим для объявления возвращающих табличные значения параметра.  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Изменение данных с помощью возвращающих табличные значения параметров (Transact-SQL)  
 Возвращающие табличные значения параметры могут использоваться в изменения данных на основе набора, которые касаются нескольких строк путем выполнения одной инструкции. Например можно выбрать все строки в табличное значение параметра и вставить их в таблицу базы данных или можно создать инструкцию update, соединяя табличное значение параметра на таблицу, которую требуется обновить.  
  
 Следующая инструкция Transact-SQL UPDATE демонстрируется использование возвращающих табличные значения параметра, присоединив ее в таблицу Categories. При использовании табличное значение параметра с СОЕДИНЕНИЕМ в предложении FROM, необходимо также псевдоним, как показано ниже, где табличное значение параметра — псевдоним «EC»:  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 В этом примере Transact-SQL демонстрируется выбор строк из табличное значение параметра для выполнения инструкции INSERT в одной операции с множествами.  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Ограничения возвращающих табличные значения параметров  
 Существует несколько ограничений для параметров, возвращающих табличные значения.  
  
-   Определяемые пользователем функции, нельзя передать табличное значение параметров.  
  
-   Возвращающие табличные значения параметры можно индексировать только для поддержки ограничений UNIQUE или PRIMARY KEY. SQL Server не ведет статистику для возвращающих табличные значения параметров.  
  
-   Возвращающие табличные значения параметров доступны только для чтения, в коде Transact-SQL. Не удается обновить значения столбцов в строках возвращающего табличное значение параметра и не удается добавить или удалить строки. Чтобы изменить данные, передается в хранимую процедуру или параметризованную инструкцию через возвращающий табличное значение параметра, необходимо вставить данные во временную таблицу или табличную переменную.  
  
-   Инструкции ALTER TABLE нельзя использовать для изменения структуры возвращающего табличное значение параметров.
-   Можно осуществлять потоковую передачу больших объектов в табличное значение параметра.  
  
## <a name="configuring-a-table-valued-parameter"></a>Настройка параметров, возвращающих табличные значения  
 Начиная с Microsoft JDBC Driver 6.0 для SQL Server, табличное значение параметров поддерживаются параметризованные инструкции или хранимой процедуры с заданными параметрами. Возвращающие табличные значения параметров можно заполняется из SQLServerDataTable, из результирующего набора или от пользователя предоставить реализацию интерфейса ISQLServerDataRecord. При задании табличное значение параметра для подготовленного запроса, необходимо указать имя типа, которое должно совпадать с именем совместимого типа, созданного ранее на сервере.  
  
 В следующих фрагментах кода демонстрируется настройка табличное значение параметра с SQLServerPreparedStatement и SQLServerCallableStatement для вставки данных. Здесь sourceTVPObject может быть SQLServerDataTable, результирующий набор или ISQLServerDataRecord объекта. В примерах предполагается активного объекта соединения является соединение.  
  
```  
// Using table-valued parameter with a SQLServerPreparedStatement.  
SQLServerPreparedStatement pStmt =   
    (SQLServerPreparedStatement) connection.prepareStatement(“INSERT INTO dbo.Categories SELECT * FROM ?”);  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);  
pStmt.execute();  
```  
  
```  
// Using table-valued parameter with a SQLServerCallableStatement.  
SQLServerCallableStatement pStmt =   
    (SQLServerCallableStatement) connection.prepareCall("exec usp_InsertCategories ?");       
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);;  
pStmt.execute();  
```  
  
> [!NOTE]  
>  В разделе **возвращающего табличное значение параметра API для драйвера JDBC** ниже полный список интерфейсов API, доступные для настройки параметров, возвращающих табличные значения.  
  
## <a name="passing-a-table-valued-parameter-as-a-sqlserverdatatable-object"></a>Передача возвращающего табличное значение параметра как объект SQLServerDataTable  
 Начиная с Microsoft JDBC Driver 6.0 для SQL Server, класс SQLServerDataTable представляет таблицу в памяти реляционных данных. В этом примере демонстрируется создание возвращающих табличные значения параметра из данных в памяти, с помощью объекта SQLServerDataTable. Код сначала создает объект SQLServerDataTable, определяет его схемы и заполняет таблицу данных. Затем в коде настраивается SQLServerPreparedStatement, передает этой таблицы данных в качестве табличное значение параметра для SQL Server.  
  
```  
// Assumes connection is an active Connection object.  
  
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
>  В разделе **возвращающего табличное значение параметра API для драйвера JDBC** ниже полный список интерфейсов API, доступные для настройки параметров, возвращающих табличные значения.  
  
## <a name="passing-a-table-valued-parameter-as-a-resultset-object"></a>Передача возвращающего табличное значение параметра как объект результирующего набора  
 В этом примере демонстрируется способ создания потока строк данных из результирующего набора параметров, возвращающих табличные значения. Код сначала получает данные из исходной таблицы в создает объект SQLServerDataTable, определяет его схемы и заполняет таблицу данных. Затем в коде настраивается SQLServerPreparedStatement, передает этой таблицы данных в качестве табличное значение параметра для SQL Server.  
  
```  
// Assumes connection is an active Connection object.  
  
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
>  В разделе **возвращающего табличное значение параметра API для драйвера JDBC** ниже полный список интерфейсов API, доступные для настройки параметров, возвращающих табличные значения.  
  
## <a name="passing-a-table-valued-parameter-as-an-isqlserverdatarecord-object"></a>Передача возвращающего табличное значение параметра как объект ISQLServerDataRecord  
 Начиная с Microsoft JDBC Driver 6.0 для SQL Server, новый интерфейс ISQLServerDataRecord доступен для потоковой передачи данных (в зависимости от того, как пользователь предоставляет реализацию для него) с помощью возвращающих табличные значения параметра. В следующем примере показано, как реализовать интерфейс ISQLServerDataRecord и как передать в качестве параметра, возвращающего табличное. Для простоты в следующем примере передается только одну строку с жестко запрограммированные значения для возвращающих табличные значения параметра. В идеальном случае пользователь будет реализовывать этот интерфейс для передачи строк из любого источника, например из текстовых файлов.  
  
```  
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
>  В разделе **возвращающего табличное значение параметра API для драйвера JDBC** ниже полный список интерфейсов API, доступные для настройки параметров, возвращающих табличные значения.  
    
## <a name="table-valued-parameter-api-for-the-jdbc-driver"></a>Табличное значение параметра API для драйвера JDBC  
 **SQLServerMetaData**  
  
 Этот класс представляет метаданные для столбца. Используется в интерфейсе ISQLServerDataRecord для передачи метаданных столбца табличное значение параметра. Доступны следующие методы этого класса:  
  
|Название|Описание|  
|----------|-----------------|  
|открытый SQLServerMetaData (columnName строки, int sqlType, int точности, масштаба int, логическое useServerDefault, логическое isUniqueKey, SQLServerSortOrder sortOrder, int sortOrdinal)|Инициализирует новый экземпляр SQLServerMetaData указанное имя столбца, тип sql, точность, масштаб и сервера по умолчанию. Эта форма конструктора поддерживает табличное значение параметров, что позволяет указывать, если столбец уникален в возвращающих табличные значения параметра, порядок сортировки для столбца и порядковый номер столбца сортировки. <br><br>useServerDefault - указывает, если этот столбец следует использовать значение сервера по умолчанию; Значение по умолчанию — false.<br>isUniqueKey - указывает, является ли столбец в табличное значение параметра уникальным; Значение по умолчанию — false.<br>sortOrder - указывает порядок сортировки для столбца; Значение по умолчанию — SQLServerSortOrder.Unspecified.<br>sortOrdinal - указывает порядковый номер столбца сортировки; sortOrdinal начинается с 0; Значение по умолчанию — -1.|
|открытый SQLServerMetaData (columnName строки, int sqlType)|Инициализирует новый экземпляр SQLServerMetaData, используя имя столбца и тип sql.|  
|открытый SQLServerMetaData (columnName строки, int sqlType, int точность, масштаб int)|Инициализирует новый экземпляр SQLServerMetaData, используя имя столбца, тип sql, точность и масштаб.|  
|Открытый SQLServerMetaData (SQLServerMetaData sqlServerMetaData)|Инициализирует новый экземпляр SQLServerMetaData передний план другого объекта SQLServerMetaData.|  
|открытый getColumName() строки|Возвращает имя столбца.|  
|открытые int getSqlType()|Возвращает тип sql java.|  
|открытые int getPrecision()|Возвращает точность типа, передаваемый в столбце.|  
|открытые int getScale()|Возвращает масштаб типа, передаваемый в столбце.|  
|открытый getSortOrder() SQLServerSortOrder|Получает порядок сортировки.|
|открытые int getSortOrdinal()|Возвращает порядковый номер сортировки.|
|открытые логическое isUniqueKey()|Указывает, является ли столбец уникальным.|
|открытые логическое useServerDefault()|Возвращает осуществляет ли столбец использует значение сервера по умолчанию.|
  
 **SQLServerSortOrder**
 
 Перечисление, которое определяет порядок сортировки. Допустимые значения — по возрастанию, по убыванию и не указано. 
  
 **SQLServerDataTable**  
  
 Этот класс представляет таблицу данных в памяти для использования с табличное значение параметров. Доступны следующие методы этого класса:  
  
|Название|Описание|  
|----------|-----------------|  
|Открытые SQLServerDataTable()|Инициализирует новый экземпляр SQLServerDataTable.|  
|открытые итератора < операция\<целое число со знаком, Object [] >> getIterator()|Извлекает итератор для строк в таблице данных.|  
|открытый addColumnMetadata void (columnName строки, int sqlType)|Добавляет метаданные для указанного столбца.|  
|открытый addColumnMetadata void (SQLServerDataColumn столбец)|Добавляет метаданные для указанного столбца.|  
|открытого метода addRow void (значений объектов...)|Добавляет одну строку данных в таблице данных.|  
|открытые карты\<целое число со знаком, SQLServerDataColumn > getColumnMetadata()|Извлекает метаданные столбца этой таблицы данных.|
|открытые методы clear() void |Очищает этой таблицы данных. |  
  
 **SQLServerDataColumn**  
  
 Этот класс представляет столбец из таблицы данных в памяти, представленной SQLServerDataTable. Доступны следующие методы этого класса:  
  
|Название|Описание|  
|----------|-----------------|  
|открытый SQLServerDataColumn (columnName строки, int sqlType)|Инициализирует новый экземпляр SQLServerDataColumn с именем столбца и типом.|  
|открытый getColumnName() строки|Возвращает имя столбца.|  
|открытые int getColumnType()|Возвращает тип столбца.|  
  
 **ISQLServerDataRecord**  
  
 Этот класс представляет интерфейс, который пользователи могут реализовать для потоковой передачи данных для параметров, возвращающих табличные значения. Доступны следующие методы этого интерфейса:  
  
|Название|Описание|  
|----------|-----------------|  
|открытый SQLServerMetaData getColumnMetaData (int, столбец);|Извлекает метаданные столбца индекса заданного столбца.|  
|открытые int getColumnCount();|Возвращает общее число столбцов.|  
|открытый getRowData() объекта [];|Получает данные для текущей строки в виде массива объектов.|  
|открытые логическое next();|Переходит на следующую строку. Возвращает значение True, если перемещение выполнено успешно, а следующую строку, значение false в противном случае.|  
  
 **SQLServerPreparedStatement**  
  
 Следующие методы были добавлены к этому классу, для поддержки передачи параметров, возвращающих табличные значения.  
  
|Название|Описание|  
|----------|-----------------|  
|открытые окончательного void setStructured (int parameterIndex, tvpName строку, SQLServerDataTable tvpDataTbale)|Заполняет возвращающей табличное значение параметр с таблицей данных. Индекс параметра должно parameterIndex, tvpName — это имя табличное значение параметра, и tvpDataTable объект источника данных таблицы.|  
|открытые окончательного void setStructured (int parameterIndex, tvpName строку, tvpResultSet результирующий набор)|Возвращающая табличное значение параметра заполняет набор результатов, полученных из другой таблицы. Индекс параметра должно parameterIndex, tvpName — имя табличное значение параметра, и tvpResultSet исходный объект результирующего набора.|  
|открытые окончательного void setStructured (int parameterIndex, tvpName строку, ISQLServerDataRecord tvpDataRecord)|Заполняет возвращающей табличное значение параметр с ISQLServerDataRecord объекта. ISQLServerDataRecord используется для потоковой передачи данных и пользователь решает, как его использовать. parameterIndex индекс параметра, tvpName — имя табличное значение параметра, который tvpDataRecord ISQLServerDataRecord объекта.|  
  
 **SQLServerCallableStatement**  
  
 Следующие методы были добавлены к этому классу, для поддержки передачи параметров, возвращающих табличные значения.  
  
|Название|Описание|  
|----------|-----------------|  
|открытые окончательного void setStructured (paratemeterName строка, строка tvpName, SQLServerDataTable tvpDataTable)|Заполняет возвращающей табличное значение параметра, передаваемое хранимой процедуры с таблицей данных. Имя параметра должно paratemeterName, tvpName — имя типа возвращающего табличное значение Параметра, и tvpDataTable объект таблицы данных.|  
|открытые окончательного void setStructured (paratemeterName строка, строка tvpName, tvpResultSet результирующий набор)|Заполняет возвращающей табличное значение параметра, передаваемое хранимой процедуры с набором результатов, полученных из другой таблицы. paratemeterName — это имя параметра, tvpName — имя типа возвращающего табличное значение Параметра и tvpResultSet является исходный объект результирующего набора.|  
|открытые окончательного void setStructured (paratemeterName строка, строка tvpName, ISQLServerDataRecord tvpDataRecord)|Заполняет возвращающей табличное значение параметра, передаваемое хранимой процедуры с ISQLServerDataRecord объекта. ISQLServerDataRecord используется для потоковой передачи данных и пользователь решает, как его использовать. paratemeterName — это имя параметра, tvpName — имя типа возвращающего табличное значение Параметра и tvpDataRecord — это объект ISQLServerDataRecord.|  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
