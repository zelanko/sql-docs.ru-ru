---
title: Использование расширенных типов данных | Документация Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b39461d3-48d6-4048-8300-1a886c00756d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b794a8c93fd7a9c83e783a04999cbeb8a9e58f48
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52510503"
---
# <a name="using-advanced-data-types"></a>Использование расширенных типов данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] расширенные типы данных JDBC служат для преобразования типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в форматы, распознаваемые языком программирования Java.  
  
## <a name="remarks"></a>Remarks

В следующей таблице перечислены все стандартные сопоставления между расширенными типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], типами данных JDBC, и типами данных языка программирования Java.  
  
|Типы SQL Server|Типы JDBC (java.sql.Types)|Типы языка Java|  
|----------------------|-----------------------------------|-------------------------|  
|varbinary(max)<br /><br /> image|LONGVARBINARY|byte[] \(по умолчанию), Blob, InputStream, String|  
|text<br /><br /> varchar(max)|LONGVARCHAR|String (по умолчанию), Clob, InputStream|  
|ntext<br /><br /> nvarchar(max)|LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0)|String (по умолчанию), Clob, NClob (Java SE 6.0)|  
|xml|LONGVARCHAR<br /><br /> SQLXML (Java SE 6.0)|String (по умолчанию), InputStream, Clob, byte[],Blob, SQLXML (Java SE 6.0)|  
|Пользовательский тип<sup>1</sup>|VARBINARY|String (по умолчанию), byte[], InputStream|  
  
<sup>1</sup> [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает отправку и получение пользовательских типов CLR в виде двоичных данных, но не поддерживает работу с метаданными CLR.  
  
В следующих разделах приведены примеры использования драйвера JDBC и расширенных типов данных.  
  
## <a name="blob-and-clob-and-nclob-data-types"></a>Типы данных BLOB, CLOB и NCLOB

Драйвер JDBC реализует все методы интерфейсов java.sql.Blob, java.sql.Clob и java.sql.NClob.  
  
> [!NOTE]  
> Значения CLOB могут использоваться с типами данных больших значений [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий. В частности, типы CLOB могут использоваться с **varchar(max)** и **nvarchar(max)** типы данных типов больших двоичных ОБЪЕКТОВ может использоваться с **varbinary(max)** и **изображения**  типы данных, а типы NCLOB могут использоваться с **ntext** и **nvarchar(max)**.  

## <a name="large-value-data-types"></a>Типы данных большого объема

В ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работа с типами данных большого объема требовала особого подхода. Типы данных больших значений — это типы, размер которых превышает максимальный размер строки в 8 КБ. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] введен описатель max для типов данных **varchar**, **nvarchar** и **varbinary**, который обеспечивает хранение значений размером до 2^31 байт. Столбцы таблицы и переменные [!INCLUDE[tsql](../../includes/tsql-md.md)] могут указывать типы данных **varchar(max)**, **nvarchar(max)** и **varbinary(max)**.  

В большинстве случаев работа с типами данных большого объема предполагает их извлечение из базы данных или добавление в базу данных. В следующих разделах описываются различные способы выполнения этих задач.  

### <a name="retrieving-large-value-types-from-a-database"></a>Извлечение типов данных большого объема из базы данных

Извлечь тип недвоичных данных большого объема, например типа данных **varchar(max)** из базы данных, можно путем считывания данных в виде потока символов. В следующем примере для извлечения данных из базы данных и их возвращения в виде результирующего набора используется метод [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) класса [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Затем для считывания данных большого объема из результирующего набора используется метод [getCharacterStream](../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md) класса [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).  

```java
ResultSet rs = stmt.executeQuery("SELECT TOP 1 * FROM Test1");  
rs.next();  
Reader reader = rs.getCharacterStream(2);  
```

> [!NOTE]
> Этот же подход можно использовать также для **текст**, **ntext**, и **nvarchar(max)** типов данных.  

Извлечь тип двоичных данных большого объема, например типа данных **varbinary(max)** из базы данных, можно несколькими способами. Эффективнее всего считать данные в виде двоичного потока следующим образом:  

```java
ResultSet rs = stmt.executeQuery("SELECT photo FROM mypics");  
rs.next();  
InputStream is = rs.getBinaryStream(2);  
```

Кроме того, для считывания данных в виде байтового массива можно следующим образом использовать метод [getBytes](../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md):  

```java
ResultSet rs = stmt.executeQuery("SELECT photo FROM mypics");  
rs.next();  
byte [] b = rs.getBytes(2);  
```

> [!NOTE]  
> Также можно считать данные в виде BLOB. Однако это менее эффективно, чем два предыдущих способа.  

### <a name="adding-large-value-types-to-a-database"></a>Добавление типов данных большого объема в базу данных.

Драйвер JDBC хорошо справляется с загрузкой больших объемов данных при наличии достаточного объема памяти. В противном случае рекомендуется использовать потоковую передачу. Тем не менее, эффективнее всего загружать большие объемы данных с помощью потоковых интерфейсов.  

Также можно использовать передачу в виде строки или байтов следующим образом:  

```java
PreparedStatement pstmt = con.prepareStatement("INSERT INTO test1 (c1_id, c2_vcmax) VALUES (?, ?)");  
pstmt.setInt(1, 1);  
pstmt.setString(2, htmlStr);  
pstmt.executeUpdate();  
```

> [!NOTE]  
> Этот подход также может использоваться для значений, которые хранятся в **текст**, **ntext**, и **nvarchar(max)** столбцов.  

При наличии на сервере библиотеки изображений и при необходимости загрузки целых двоичных файлов изображений в столбец **varbinary(max)** эффективнее всего использовать драйвер JDBC, организуя потоки напрямую следующим образом:  

```java
try (PreparedStatement pstmt = con.prepareStatement("INSERT INTO test1 (Col1, Col2) VALUES(?,?)")) { 
  File inputFile = new File("CLOBFile20mb.jpg");  
  try (FileInputStream inStream = new FileInputStream(inputFile)) {
    int id = 1;  
    pstmt.setInt(1,id);  
    pstmt.setBinaryStream(2, inStream);  
    pstmt.executeUpdate();
  }
}
```

> [!NOTE]  
> Методы CLOB и BLOB для загрузки больших объемов данных неэффективны.  

### <a name="modifying-large-value-types-in-a-database"></a>Изменение типов данных большого объема в базе данных.

В большинстве случаев для обновления или изменения больших значений в базе данных рекомендуется передавать параметры через классы [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) с помощью таких команд [!INCLUDE[tsql](../../includes/tsql-md.md)], как `UPDATE`, `WRITE` и `SUBSTRING`.  

Если нужно заменить экземпляр слова в крупном текстовом файле, например в архивном HTML-файле, можно воспользоваться объектом Clob следующим образом:  

```java
String SQL = "SELECT * FROM test1;";  
try (Statement stmt = con.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE)
     ResultSet rs = stmt.executeQuery(SQL)) {
  rs.next();

  Clob clob = rs.getClob(2);  
  long pos = clob.position("dog", 1);  
  clob.setString(pos, "cat");  
  rs.updateClob(2, clob);  
  rs.updateRow();  
}
```

Кроме того, можно выполнить все операции на сервере и просто передать параметры в подготовленную инструкцию UPDATE.  

Дополнительные сведения о типах данных большого объема ищите в разделе «Использование типов данных большого объема» электронной документации по Microsoft SQL Server.  

## <a name="xml-data-type"></a>Тип данных XML

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит тип данных **xml**, который позволяет хранить XML-документы и фрагменты в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Тип данных **xml** — это встроенный в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных, несколько напоминающий другие встроенные типы данных, такие как **int** и **varchar**. Аналогично другим встроенным типам, типы данных **xml** можно использовать следующим образом: как тип переменной, тип параметра, тип возвращаемой функции или тип столбца при создании таблицы, а также в функциях CAST и CONVERT [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
В драйвере JDBC тип данных **xml** может быть сопоставлен со строкой, байтовым массивом, потоком или объектом CLOB, BLOB или SQLXML. По умолчанию задана строка. Для драйвера JDBC, начиная с версии 2.0, обеспечивается поддержка API-интерфейса JDBC 4.0, что позволяет использовать интерфейс SQLXML. Интерфейс SQLXML определяет методы для обмена данными XML и их обработки. **SQLXML** сопоставляется с типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **xml** тип данных. Дополнительные сведения о считывании XML-данных из реляционной базы данных и записи их в нее с типом данных Java **SQLXML** см. в разделе [Поддержка данных XML](../../connect/jdbc/supporting-xml-data.md).  
  
Благодаря реализации типа данных **xml** в драйвере JDBC обеспечена поддержка следующих возможностей:  
  
- Доступ к XML как к стандартным строкам Java UTF-16 для большинства общепринятых методик программирования.  
  
- Ввод UTF-8 и других XML-данных с 8-битным кодированием.  
  
- Доступ к XML как к байтовому массиву с ведущей меткой следования байтов (BOM) при кодировании в UTF-16 для взаимообмена с другими средствами обработками XML и файлами на диске.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требует для XML в кодировке UTF-16 ведущую метку следования байтов (BOM). Приложение должно использовать эту метку при указании значений параметров XML в виде байтовых массивов. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда выводит XML-значения как строки в кодировке UTF-16 без метки следования байтов и без внедренного объявления кодировки. Если значения XML извлекаются в формате byte[], BinaryStream или Blob, то для значения ожидается метка следования байтов UTF-16.  
  
Дополнительные сведения о типе данных **xml** можно найти в разделе "Тип данных XML" электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="user-defined-data-type"></a>Пользовательский тип данных  

Введение определяемых пользователем типов (UDT) в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] совершенствует систему типов SQL, позволяя пользователю сохранять объекты и настраиваемые структуры данных в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Определяемые пользователем типы могут содержать несколько типов данных, и их поведение может отличаться от традиционных псевдонимов типов данных, которые состоят из одного системного типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Определяемые пользователем типы данных определяются с помощью любого из языков, которые поддерживаются средой Microsoft .NET CLR и формируют проверяемый код. Это языки Microsoft Visual C# и Visual Basic .NET. Данные предоставляются в виде полей и свойств класса или структуры на базе платформы .NET Framework, а особенности работы определяются методами класса или структуры.  
  
В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользовательские типы данных можно использовать в качестве идентификатора столбцов таблицы, как переменную в пакете [!INCLUDE[tsql](../../includes/tsql-md.md)] или как аргумент функции [!INCLUDE[tsql](../../includes/tsql-md.md)] или хранимой процедуры.  
  
Дополнительные сведения о применении пользовательских типов данных см. в разделе "Использование и изменение экземпляров пользовательских типов" в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:

[Основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
