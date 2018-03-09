---
title: "Использование расширенных типов данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b39461d3-48d6-4048-8300-1a886c00756d
caps.latest.revision: "58"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5ca19754f3332c1832405085ad1b04fb36380bd9
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="using-advanced-data-types"></a>Использование расширенных типов данных
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Использует расширенные типы данных JDBC для преобразования [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] типов данных в формат, распознаваемый Java языка программирования.  
  
## <a name="remarks"></a>Замечания  
 В следующей таблице перечислены все стандартные сопоставления между расширенными [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], JDBC и типами данных языка программирования Java.  
  
|Типы SQL Server|Типы JDBC (java.sql.Types)|Типы языка Java|  
|----------------------|-----------------------------------|-------------------------|  
|varbinary(max)<br /><br /> image|LONGVARBINARY|Byte [] \(по умолчанию), Blob, InputStream, строка|  
|text<br /><br /> varchar(max)|LONGVARCHAR|String (по умолчанию), Clob, InputStream|  
|ntext<br /><br /> nvarchar(max)|LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0)|String (по умолчанию), Clob, NClob (Java SE 6.0)|  
|xml|LONGVARCHAR<br /><br /> SQLXML (Java SE 6.0)|String (по умолчанию), InputStream, Clob, byte[],Blob, SQLXML (Java SE 6.0)|  
|Определяемый пользователем тип<sup>1</sup>|VARBINARY|String (по умолчанию), byte[], InputStream|  
  
 <sup>1</sup> [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает отправку и получение определяемых пользователем типов CLR как двоичные данные, но не поддерживает операции с метаданными CLR.  
  
 В следующих разделах приведены примеры использования драйвера JDBC и расширенных типов данных.  
  
## <a name="blob-and-clob-and-nclob-data-types"></a>Типы данных BLOB, CLOB и NCLOB  
 Драйвер JDBC реализует все методы интерфейсов java.sql.Blob, java.sql.Clob и java.sql.NClob.  
  
> [!NOTE]  
>  Значения CLOB могут использоваться с [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] (или более поздней версии) типы данных больших значений. В частности, типы CLOB могут использоваться с **varchar(max)** и **nvarchar(max)** типы данных типов больших двоичных ОБЪЕКТОВ можно использовать с **varbinary(max)** и **изображения**  типы данных, а типы NCLOB могут использоваться с **ntext** и **nvarchar(max)**.  
  
## <a name="large-value-data-types"></a>Типы данных большого объема  
 В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]работа с данными большого размера типов требовала особого подхода. Типы данных больших значений — это типы, размер которых превышает максимальный размер строки в 8 КБ. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Представляет описатель max для **varchar**, **nvarchar**, и **varbinary** типы данных, чтобы разрешить хранение значений размером до 2 ^ 31 байт. Столбцы таблицы и [!INCLUDE[tsql](../../includes/tsql_md.md)] можно указать переменные **varchar(max)**, **nvarchar(max)**, или **varbinary(max)** типов данных.  
  
 В большинстве случаев работа с типами данных большого объема предполагает их извлечение из базы данных или добавление в базу данных. В следующих разделах описываются различные способы выполнения этих задач.  
  
### <a name="retrieving-large-value-types-from-a-database"></a>Извлечение типов данных большого объема из базы данных  
 Если извлечь тип недвоичных данных большого объема, например **varchar(max)** тип данных — из базы данных, одним из подходов является считывания данных в виде потока символов. В следующем примере [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) метод [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класс используется для получения данных из базы данных и возвращать в виде результирующего набора. Затем [getCharacterStream](../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md) метод [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) класс используется для считывания данных большого объема из результирующего набора.  
  
```  
ResultSet rs = stmt.executeQuery("SELECT TOP 1 * FROM Test1");  
rs.next();  
Reader reader = rs.getCharacterStream(2);  
```  
  
> [!NOTE]  
>  Этот же подход можно использовать также для **текст**, **ntext**, и **nvarchar(max)** типов данных.  
  
 При извлечении типа двоичных данных больших значений, таких как **varbinary(max)** тип данных — из базы данных, существует несколько подходов, которые можно предпринять. Эффективнее всего считать данные в виде двоичного потока следующим образом:  
  
```  
ResultSet rs = stmt.executeQuery("SELECT photo FROM mypics");  
rs.next();  
InputStream is = rs.getBinaryStream(2);  
```  
  
 Можно также использовать [getBytes](../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md) метод для чтения данных в виде массива байтов, как описано ниже:  
  
```  
ResultSet rs = stmt.executeQuery("SELECT photo FROM mypics");  
rs.next();  
byte [] b = rs.getBytes(2);  
```  
  
> [!NOTE]  
>  Также можно считать данные в виде BLOB. Однако это менее эффективно, чем два предыдущих способа.  
  
### <a name="adding-large-value-types-to-a-database"></a>Добавление типов данных большого объема в базу данных.  
 Драйвер JDBC хорошо справляется с загрузкой больших объемов данных при наличии достаточного объема памяти. В противном случае рекомендуется использовать потоковую передачу. Тем не менее, эффективнее всего загружать большие объемы данных с помощью потоковых интерфейсов.  
  
 Также можно использовать передачу в виде строки или байтов следующим образом:  
  
```  
PreparedStatement pstmt = con.prepareStatement("INSERT INTO test1 (c1_id, c2_vcmax) VALUES (?, ?)");  
pstmt.setInt(1, 1);  
pstmt.setString(2, htmlStr);  
pstmt.executeUpdate();  
```  
  
> [!NOTE]  
>  Такой подход также может использоваться для значений, хранящихся в **текст**, **ntext**, и **nvarchar(max)** столбцов.  
  
 При наличии на сервере библиотеки изображений и при необходимости загрузить целые двоичные файлы изображений для **varbinary(max)** , наиболее эффективный метод с помощью драйвера JDBC будет использовать потоки напрямую, как описано ниже:  
  
```  
PreparedStatement pstmt = con.prepareStatement("INSERT INTO test1 (Col1, Col2) VALUES(?,?)");  
File inputFile = new File("CLOBFile20mb.jpg");  
FileInputStream inStream = new FileInputStream(inputFile);  
int id = 1;  
pstmt.setInt(1,id);  
pstmt.setBinaryStream(2, inStream);  
pstmt.executeUpdate();  
inStream.close();  
```  
  
> [!NOTE]  
>  Методы CLOB и BLOB для загрузки больших объемов данных неэффективны.  
  
### <a name="modifying-large-value-types-in-a-database"></a>Изменение типов данных большого объема в базе данных.  
 В большинстве случаев для обновления или изменения больших значений в базе данных рекомендуется передавать параметра через [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) классы с помощью [!INCLUDE[tsql](../../includes/tsql_md.md)] такие команды как UPDATE, WRITE и SUBSTRING.  
  
 Если нужно заменить экземпляр слова в крупном текстовом файле, например в архивном HTML-файле, можно использовать объект Clob, как показано ниже:  
  
```  
String SQL = "SELECT * FROM test1;";  
Statement stmt = con.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE);  
ResultSet rs = stmt.executeQuery(SQL);  
rs.next();  
  
Clob clob = rs.getClob(2);  
long pos = clob.position("dog", 1);  
clob.setString(pos, "cat");  
rs.updateClob(2, clob);  
rs.updateRow();  
```  
  
 Кроме того, можно выполнить все операции на сервере и просто передать параметры в подготовленную инструкцию UPDATE.  
  
 Дополнительные сведения о типах данных большого объема ищите в разделе «Использование типов данных большого объема» электронной документации по Microsoft SQL Server.  
  
## <a name="xml-data-type"></a>Тип данных XML  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]предоставляет **xml** тип данных, который позволяет хранить XML-документы и фрагменты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных. **Xml** тип данных является встроенным типом данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]и в чем-то напоминающий другие встроенные типы, такие как **int** и **varchar**. Как и другие встроенные типы можно использовать **xml** тип данных, как тип столбца при создании таблицы, как тип переменной, тип параметра или типа возвращаемого функцией значения; или в [!INCLUDE[tsql](../../includes/tsql_md.md)] функций CAST и CONVERT.  
  
 В драйвере JDBC **xml** могут быть сопоставлены типу данных String, массив байтов, поток, объект CLOB, BLOB или SQLXML. По умолчанию задана строка. Для драйвера JDBC, начиная с версии 2.0, обеспечивается поддержка API-интерфейса JDBC 4.0, что позволяет использовать интерфейс SQLXML. Интерфейс SQLXML определяет методы для обмена данными XML и их обработки. **SQLXML** сопоставляется с типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **xml** тип данных. Дополнительные сведения о том, как на чтение и запись XML-данных из реляционной базы данных с **SQLXML** типом данных Java см [XML-данных с поддержкой](../../connect/jdbc/supporting-xml-data.md).  
  
 Реализация **xml** тип данных в драйвере JDBC обеспечивает поддержку для следующего:  
  
-   Доступ к XML как к стандартным строкам Java UTF-16 для большинства общепринятых методик программирования.  
  
-   Ввод UTF-8 и других XML-данных с 8-битным кодированием.  
  
-   Доступ к XML как к байтовому массиву с ведущей меткой следования байтов (BOM) при кодировании в UTF-16 для взаимообмена с другими средствами обработками XML и файлами на диске.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]начальные Спецификации требует для XML в кодировке UTF-16. Приложение должно использовать эту метку при указании значений параметров XML в виде байтовых массивов. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]всегда выводит XML-значения как UTF-16 без метки следования байтов строки или встроенным объявлением кодировки. Если значения XML извлекаются в формате byte[], BinaryStream или Blob, то для значения ожидается метка следования байтов UTF-16.  
  
 Дополнительные сведения о **xml** тип данных, в разделе «тип данных xml» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="user-defined-data-type"></a>Пользовательский тип данных  
 Введение определяемых пользователем типов (UDT) в [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] расширяет систему типов SQL, позволяя пользователю сохранять объекты и пользовательские структуры данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных. Определяемые пользователем типы могут содержать несколько типов данных, и их поведение может отличаться от традиционных псевдонимов типов данных, которые состоят из одного системного типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Определяемые пользователем типы данных определяются с помощью любого из языков, которые поддерживаются средой Microsoft .NET CLR и формируют проверяемый код. Это языки Microsoft Visual C# и Visual Basic .NET. Данные предоставляются в виде полей и свойств класса или структуры на базе платформы .NET Framework, а особенности работы определяются методами класса или структуры.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], определяемого пользователем ТИПА можно использовать в качестве определения столбца таблицы, в переменной [!INCLUDE[tsql](../../includes/tsql_md.md)] пакет, или как аргумент [!INCLUDE[tsql](../../includes/tsql_md.md)] функции или хранимой процедуры.  
  
 Дополнительные сведения об определенных пользователем типов данных см. в разделе «Использование и изменение экземпляров определяемых пользователем типов» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
