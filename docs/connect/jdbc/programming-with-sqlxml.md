---
title: Программирование с SQLXML | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4d2cc57c-7293-4d92-b8b1-525e2b35f591
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 22f225799e704b7a34449bbfc69ef351cc4d4ac1
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "69027772"
---
# <a name="programming-with-sqlxml"></a>Программирование с SQLXML.
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В этом разделе описано использование методов API [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] для сохранения XML-документа в реляционной базе данных и извлечения документов из нее с помощью объектов **SQLXML**.  
  
 В этом разделе также содержатся сведения о типах объектов SQLXML и список важных рекомендаций и ограничений при работе с объектами SQLXML.  
  
## <a name="reading-and-writing-xml-data-with-sqlxml-objects"></a>Чтение и запись XML-данных с использованием объектов SQLXML  
 В следующем списке описывается использование методов API [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] для чтения и записи XML-данных с использованием объектов SQLXML.  
  
-   Для создания объекта SQLXML используйте метод [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Обратите внимание, что этот метод создает объект SQLXML без данных. Чтобы добавить данные **xml** к объекту SQLXML, вызовите один из следующих методов, определенных в интерфейсе SQLXML: setResult, setCharacterStream, setBinaryStream или setString.  
  
-   Чтобы извлечь сам объект SQLXML, используйте методы getSQLXML класса [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) или класса [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md).  
  
-   Чтобы получить данные **xml** из объекта SQLXML, вызовите один из следующих методов, определенных в интерфейсе SQLXML: getSource, getCharacterStream, getBinaryStream или getString.  
  
-   Чтобы обновить данные **xml** в объекте SQLXML, используйте метод [updateSQLXML](../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md) класса [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
-   Чтобы сохранить объект SQLXML в столбце таблицы базы данных типа **xml**, используйте методы setSQLXML класса [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) или класса [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md).  
  
 В коде с [примером типа данных SQLXML](../../connect/jdbc/sqlxml-data-type-sample.md) демонстрируется, как выполнять распространенные задачи API.  
  
## <a name="readable-and-writable-sqlxml-objects"></a>Читаемые и записываемые объекты SQLXML  
 В следующей таблице перечислены типы объектов SQLXML, поддерживаемые методами задания, считывания и обновления свойств, предоставленными JDBC API. Столбцы в таблице ссылаются на следующее:  
  
-   В столбце **Имя метода** перечислены поддерживаемые методы получения, задания и обновления в API JDBC.  
  
-   Столбец **Объект получения SQLXML** представляет объект SQLXML, созданный методом [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md) класса [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) или методом [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) класса [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
-   Столбец **Объект задания SQLXML** представляет объект SQLXML, созданный методом [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Обратите внимание, что метод задания, описанный ниже, принимает только объект SQLXML, созданный методом [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md).  
  
|Имя метода|Объект считывания SQLXML<br /><br /> (читаемый)|Объект задания SQLXML<br /><br /> (записываемый)|  
|-----------------|-------------------------------------------|-------------------------------------------|  
|CallableStatement.setSQLXML()|Не поддерживается|Поддерживается|  
|CallableStatement.setObject()|Не поддерживается|Поддерживается|  
|PreparedStatement.setSQLXML()|Не поддерживается|Поддерживается|  
|PreparedStatement.setObject()|Не поддерживается|Поддерживается|  
|ResultSet.updateSQLXML()|Не поддерживается|Поддерживается|  
|ResultSet.updateObject()|Не поддерживается|Поддерживается|  
|ResultSet.getSQLXML()|Поддерживается|Не поддерживается|  
|CallableStatement.getSQLXML()|Поддерживается|Не поддерживается|  
  
 Как показано в таблице выше, методы задания SQLXML не будут работать при использовании с читаемыми объектами SQLXML; аналогичным образом методы считывания не будут работать при использовании с записываемыми объектами SQLXML.  
  
 Если приложение вызывает метод setObject с помощью указания параметра масштаба или длины объекта SQLXML, параметр масштаба или длины пропускается.  
  
## <a name="guidelines-and-limitations-when-using-sqlxml-objects"></a>Рекомендации и ограничения, связанные с использованием объектов SQLXML  
 Приложения могут использовать объекты SQLXML для чтения и записи данных XML в базе данных. В следующем списке содержатся сведения об определенных ограничениях и рекомендациях при использовании объектов SQLXML:  
  
-   Объект SQLXML является действительным только во время выполнении транзакции, в которой он был создан.  
  
-   Объект SQLXML, полученный методом считывания, может быть использован только для чтения данных.  
  
-   Объект SQLXML, созданный методом соединения, может быть использован только для записи данных.  
  
-   Приложение может вызвать только один метод считывания на читаемом объекте SQLXML для чтения данных. После вызова метода считывания в работе всех остальных методов считывания и задания на этом же объекте SQLXML произойдет ошибка.  
  
-   Приложение может вызвать метод free на объекте SQLXML только после его чтения или записи. Однако еще сохраняется возможность обработки возвращенного потока или источника, если базовый столбец или параметр активен. Если базовый столбец или параметр становится неактивен, то будет закрыт поток или источник, связанный с объектом SQLXML. Если базовый столбец или параметр более не является допустимым, то базовые данные будут недоступны для методов считывания Stream, Simple API for XML (SAX) и Streaming API for XML (StAX).  
  
-   Приложение может вызвать только один метод задания на записываемом объекте SQLXML. После вызова метода задания в работе всех остальных методов считывания и задания на этом же объекте SQLXML произойдет ошибка.  
  
-   Чтобы задать данные для объекта SQLXML, приложение должно использовать соответствующий метод задания и функции в возвращенном объекте.  
  
-   Методы getSQLXML классов [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) и [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) возвращают данные **null**, если для базового столбца задано значение **null**.  
  
-   Объекты метода задания являются допустимыми в период выполнения соединения, в котором они были созданы.  
  
-   Приложения не могут задавать значение **null** с помощью методов задания, предоставленных интерфейсом SQLXML. Приложения могут задавать пустую строку с помощью методов задания, предоставленных в интерфейсе SQLXML. Чтобы задать значение **null**, приложения должны вызвать одно из следующего.  
  
    -   Методы setNull классов [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) и [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).  
  
    -   Методы setObject классов [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) и [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).  
  
    -   Методы setSQLXML классов [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) и [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) со значением параметра **null**.  
  
-   При работе с XML-документами рекомендуется использовать средства синтаксического анализа Simple API for XML (SAX) и Streaming API for XML (StAX) вместо средств синтаксического анализа модели DOM, т.к. они обеспечивают более высокий уровень производительности.  
  
 Средства синтаксического анализа XML не могут обрабатывать пустые значения. Однако SQL Server позволяет приложениям извлекать и сохранять пустые значения в столбцах баз данных типа данных XML. Это означает, что если базовое значение пустое, то при синтаксическом анализе XML-данных средство синтаксического анализа вызовет исключение. При использовании выходных значений DOM драйвер JDBC обрабатывает это исключение и вызывает ошибку. При работе с выходными значениями SAX и Stax ошибка вызывается средством синтаксического анализа напрямую.  
  
## <a name="adaptive-buffering-and-sqlxml-support"></a>Адаптивная буферизация и поддержка SQLXML  
 Двоичные и символьные потоки, возвращаемые объектом SQLXML, поддерживают режимы адаптивной и полной буферизации. С другой стороны, если средства синтаксического анализа XML не являются потоками, они не поддерживают настройки адаптивной и полной буферизации. Дополнительные сведения об использовании адаптивной буферизации см. в [этой статье](../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>См. также раздел  
 [Поддержка данных XML](../../connect/jdbc/supporting-xml-data.md)  
  
  
