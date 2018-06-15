---
title: Программирование с SQLXML | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4d2cc57c-7293-4d92-b8b1-525e2b35f591
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5cb6d2d44b9988dda28d5e9bd10db0d96467ff6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32833089"
---
# <a name="programming-with-sqlxml"></a>Программирование с SQLXML.
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В этом разделе описывается использование [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] методов API для хранения и извлечения XML документа, в и из реляционной базы данных с **SQLXML** объектов.  
  
 В этом разделе также содержатся сведения о типах объектов SQLXML и список важных рекомендаций и ограничений при работе с объектами SQLXML.  
  
## <a name="reading-and-writing-xml-data-with-sqlxml-objects"></a>Чтение и запись XML-данных с использованием объектов SQLXML  
 Следующий список описывает использование [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] методы API для чтения и записи XML-данных с использованием объектов SQLXML:  
  
-   Чтобы создать объект SQLXML, используйте [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) метод [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса. Обратите внимание, что этот метод создает объект SQLXML без данных. Чтобы добавить **xml** данных объект SQLXML, вызовите один из следующих методов, указанных в интерфейсе SQLXML: setResult, setCharacterStream, setBinaryStream, или setString.  
  
-   Чтобы извлечь сам объект SQLXML, используйте методы getSQLXML [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) класса или [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) класса.  
  
-   Для получения **xml** данными из объекта SQLXML используйте один из следующих методов, указанных в интерфейсе SQLXML: getSource getCharacterStream, getBinaryStream, или getString.  
  
-   Чтобы обновить **xml** данные в объект SQLXML, используйте [updateSQLXML](../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md) метод [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) класса.  
  
-   Чтобы сохранить объект SQLXML в столбце таблицы базы данных типа **xml**, используйте методы setSQLXML [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) класса или [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)класса.  
  
 В примере кода в [SQLXML Data Type Sample](../../connect/jdbc/sqlxml-data-type-sample.md) демонстрируется выполнение общих задач API.  
  
## <a name="readable-and-writable-sqlxml-objects"></a>Читаемые и записываемые объекты SQLXML  
 В следующей таблице перечислены типы объектов SQLXML, поддерживаемые методами задания, считывания и обновления свойств, предоставленными JDBC API. Столбцы в таблице ссылаются на следующее:  
  
-   **Имя метода** столбце перечислены поддерживаемые методы считывания, задания и обновления в JDBC API.  
  
-   **Объект считывания SQLXML** столбец представляет объект SQLXML, который создан либо с помощью [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md) метод [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) класса или [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) метод [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) класса.  
  
-   **Объект задания SQLXML** столбец представляет объект SQLXML, созданный [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) метод [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса. Обратите внимание, что указанные ниже методы setter принимать только объект SQLXML, созданный [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) метод.  
  
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
  
 Если приложение вызывает метод setObject, задав режим масштаба или параметр длины объекта SQLXML, параметр масштаба или длины пропускается.  
  
## <a name="guidelines-and-limitations-when-using-sqlxml-objects"></a>Рекомендации и ограничения при использовании объектов SQLXML  
 Приложения могут использовать объекты SQLXML для чтения и записи данных XML в базе данных. В следующем списке содержатся сведения об определенных ограничениях и рекомендациях при использовании объектов SQLXML:  
  
-   Объект SQLXML является действительным только во время выполнении транзакции, в которой он был создан.  
  
-   Объект SQLXML, полученный методом считывания, может быть использован только для чтения данных.  
  
-   Объект SQLXML, созданный методом соединения, может быть использован только для записи данных.  
  
-   Приложение может вызвать только один метод считывания на читаемом объекте SQLXML для чтения данных. После вызова метода считывания в работе всех остальных методов считывания и задания на этом же объекте SQLXML произойдет ошибка.  
  
-   Приложение может вызвать только свободного метод на объекте SQLXML, после его чтения или записи. Однако еще сохраняется возможность обработки возвращенного потока или источника, если базовый столбец или параметр активен. Если базовый столбец или параметр становится неактивен, то будет закрыт поток или источник, связанный с объектом SQLXML. Если базовый столбец или параметр более не является допустимым, то базовые данные будут недоступны для методов считывания Stream, Simple API for XML (SAX) и Streaming API for XML (StAX).  
  
-   Приложение может вызвать только один метод задания на записываемом объекте SQLXML. После вызова метода задания в работе всех остальных методов считывания и задания на этом же объекте SQLXML произойдет ошибка.  
  
-   Чтобы задать данные для объекта SQLXML, приложение должно использовать соответствующий метод задания и функции в возвращенном объекте.  
  
-   Методы getSQLXML [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) класса и [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) возвращает **null** данные, если базовые столбцы являются **null**.  
  
-   Объекты метода задания являются допустимыми в период выполнения соединения, в котором они были созданы.  
  
-   Приложения не могут установить **null** значение с помощью методов задания, предоставленных интерфейсом SQLXML. Приложения могут задавать пустую строку с помощью методов задания, предоставленных в интерфейсе SQLXML. Чтобы задать **null** значение, приложения должны вызвать одно из следующих:  
  
    -   Методы setNull [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) класса и [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) класса.  
  
    -   Методы setObject [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) класса и [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) класса.  
  
    -   Методы setSQLXML [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) класса и [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) класса **null** значение параметра.  
  
-   При работе с XML-документами рекомендуется использовать средства синтаксического анализа Simple API for XML (SAX) и Streaming API for XML (StAX) вместо средств синтаксического анализа модели DOM, т.к. они обеспечивают более высокий уровень производительности.  
  
 Средства синтаксического анализа XML не могут обрабатывать пустые значения. Однако SQL Server позволяет приложениям извлекать и сохранять пустые значения в столбцах баз данных типа данных XML. Это означает, что если базовое значение пустое, то при синтаксическом анализе XML-данных средство синтаксического анализа вызовет исключение. При использовании выходных значений DOM драйвер JDBC обрабатывает это исключение и вызывает ошибку. При работе с выходными значениями SAX и Stax ошибка вызывается средством синтаксического анализа напрямую.  
  
## <a name="adaptive-buffering-and-sqlxml-support"></a>Адаптивная буферизация и поддержка SQLXML  
 Двоичные и символьные потоки, возвращаемые объектом SQLXML, поддерживают режимы адаптивной и полной буферизации. С другой стороны, если средства синтаксического анализа XML не являются потоками, они не поддерживают настройки адаптивной и полной буферизации. Дополнительные сведения об использовании адаптивной буферизации см. в разделе [с помощью адаптивной буферизации](../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>См. также  
 [Поддержка XML-данных](../../connect/jdbc/supporting-xml-data.md)  
  
  
