---
title: Образец типа данных SQLXML | Документы Microsoft
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
ms.topic: article
ms.assetid: 8f2ff25b-71fd-46d7-b6de-d656095d2aad
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a88c102ff38b522850d333c671c37df5af3cfbe2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlxml-data-type-sample"></a>Образец типа данных SQLXML
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Это [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] образце приложения показано, как сохранить данные XML в реляционной базе данных, способ получения XML-данных из базы данных и как выполнить синтаксический анализ XML-данных с **SQLXML** типа данных.  
  
 В примерах кода в этом разделе используется Simple API-интерфейс для синтаксического анализатора XML (SAX). Интерфейс SAX ― это открытый стандарт синтаксического анализа XML-документов на основе событий. Он также предоставляет прикладной программный интерфейс для работы с XML-данными. Обратите внимание, что приложения могут использовать и другие синтаксические анализаторы XML, например модель DOM или потоковый API-интерфейс для XML (StAX) и так далее.  
  
 Модель DOM обеспечивает программное представление XML-документов, фрагментов, узлов и наборов узлов. Он также предоставляет прикладной программный интерфейс для работы с XML-данными. Схожим образом потоковый API-интерфейс для XML (StAX) ― это API-интерфейс на основе Java для синтаксического анализа XML.  
  
> [!IMPORTANT]  
>  Чтобы использовать API-интерфейс средства синтаксического анализа SAX, следует импортировать стандартную реализацию SAX из пакета javax.xml.  
  
 Файл кода для этого образца имеет имя sqlxmlExample.java и находится в следующей папке:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \samples\datatypes  
  
## <a name="requirements"></a>Требования  
 Чтобы запустить этот образец приложения, необходимо включить в параметр classpath путь к файлу sqljdbc4.jar. Если параметр classpath не включает путь к файлу sqljdbc4.jar, образец приложения вызовет исключение «Класс не найден». Дополнительные сведения о том, как задать значение переменной classpath см. в разделе [с помощью драйвера JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
 Кроме того, необходим доступ к [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образец базы данных для запуска этого образца приложения.  
  
## <a name="example"></a>Пример  
 В следующем примере образец кода устанавливает соединение для [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] базы данных, а затем вызывает метод createSampleTables.  
  
 Метод createSampleTables удаляет тестовые таблицы, TestTable1 и TestTable2, если они существуют. Затем метод вставляет две строки в TestTable1.  
  
 Кроме этого, образец кода включает следующие три метода и один дополнительный класс, который называется ExampleContentHandler.  
  
 Класс ExampleContentHandler реализует пользовательский обработчик содержимого, который определяет методы для событий анализатора.  
  
 Метод showGetters показывает, как анализировать данные в объекте SQLXML при помощи SAX, ContentHandler и XMLReader. Сначала образец кода создает экземпляр пользовательского обработчика данных, то есть ExampleContentHandler. Затем он создает и выполняет инструкцию SQL, которая возвращает набор данных из TestTable1. Далее образец кода запускает средство синтаксического анализа SAX и обрабатывает XML-данные.  
  
 Метод showSetters показывает, как задать **xml** столбца с помощью SAX, ContentHandler и ResultSet. Во-первых, он создает пустой объект SQLXML, используя [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) метод класса подключения. Затем метод поручает экземпляру обработчика содержимого записать данные в объект SQLXML. Далее пример кода записывает данные в TestTable1. И, наконец, в примере кода выполняется итерация по строкам данных, содержащихся в результирующем наборе и использует [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) метод для чтения данных XML.  
  
 Метод showTransformer показывает, как получить XML-данные из одной таблицы и вставить эти XML-данные в другую таблицу при помощи SAX и преобразователя. Сначала метод извлекает объект SLQXML из TestTable1. Затем он создает пустой объект назначения SQLXML с помощью [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) метод класса подключения. Далее метод обновляет объект назначения SQLXML и записывает XML-данные в TestTable2. И, наконец, в примере кода выполняется итерация по строкам данных, содержащихся в результирующем наборе и использует [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) метод для чтения XML-данных в TestTable2.  
  
 [!code[JDBC#UsingSQLXML1](../../connect/jdbc/codesnippet/Java/sqlxml-data-type-sample_1.java)]  
  
## <a name="see-also"></a>См. также  
 [Работа с типами данных &#40;JDBC&#41;](../../connect/jdbc/working-with-data-types-jdbc.md)  
  
  
