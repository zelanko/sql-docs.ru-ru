---
title: Образец типа данных SQLXML | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8f2ff25b-71fd-46d7-b6de-d656095d2aad
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 62f222a450798c7c685ce55f8d82e876b6e24d5f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628082"
---
# <a name="sqlxml-data-type-sample"></a>Образец типа данных SQLXML

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В этом образце приложения, использующем драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], показано, как сохранить данные XML в реляционной базе данных, как извлечь их из базы данных и выполнить их синтаксический анализ с помощью типа данных Java **SQLXML**.

В примерах кода в этом разделе используется Simple API-интерфейс для синтаксического анализатора XML (SAX). Интерфейс SAX ― это открытый стандарт синтаксического анализа XML-документов на основе событий. Он также предоставляет прикладной программный интерфейс для работы с XML-данными. Обратите внимание, что приложения могут использовать и другие синтаксические анализаторы XML, например модель DOM или потоковый API-интерфейс для XML (StAX) и так далее.

Модель DOM обеспечивает программное представление XML-документов, фрагментов, узлов и наборов узлов. Он также предоставляет прикладной программный интерфейс для работы с XML-данными. Схожим образом потоковый API-интерфейс для XML (StAX) ― это API-интерфейс на основе Java для синтаксического анализа XML.

> [!IMPORTANT]  
> Чтобы использовать API-интерфейс средства синтаксического анализа SAX, следует импортировать стандартную реализацию SAX из пакета javax.xml.

Файл кода для этого примера с именем SqlXmlDataType.java находится в следующей папке:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\datatypes
```

## <a name="requirements"></a>Требования

Чтобы запустить этот образец приложения, необходимо включить в параметр classpath путь к файлу sqljdbc4.jar. Если параметр classpath не включает путь к файлу sqljdbc4.jar, образец приложения вызовет исключение «Класс не найден». Дополнительные сведения о том, как путь к классу см. в разделе [с помощью драйвера JDBC](../../connect/jdbc/using-the-jdbc-driver.md).

Кроме этого, для запуска данного примера приложения необходим доступ к образцу базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)].

## <a name="example"></a>Пример

В следующем примере образец кода будет использоваться для соединения с базой данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] и вызова метода createSampleTables.

Метод createSampleTables удаляет тестовые таблицы, TestTable1 и TestTable2, если они существуют. Затем метод вставляет две строки в TestTable1.

Кроме этого, образец кода включает следующие три метода и один дополнительный класс, который называется ExampleContentHandler.

Класс ExampleContentHandler реализует пользовательский обработчик содержимого, который определяет методы для событий анализатора.

Метод showGetters показывает, как анализировать данные в объекте SQLXML при помощи SAX, ContentHandler и XMLReader. Сначала образец кода создает экземпляр пользовательского обработчика данных, то есть ExampleContentHandler. Затем он создает и выполняет инструкцию SQL, которая возвращает набор данных из TestTable1. Далее образец кода запускает средство синтаксического анализа SAX и обрабатывает XML-данные.

Метод showSetters показывает, как задать столбец **xml** при помощи SAX, ContentHandler и ResultSet. Сначала создается пустой объект SQLXML, используя метод класса Connection [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md). Затем метод поручает экземпляру обработчика содержимого записать данные в объект SQLXML. Далее пример кода записывает данные в TestTable1. Наконец, образец кода выполняет проход по строкам данных, содержащимся в результирующем наборе, и используется метод [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) для прочтения XML-данных.

Метод showTransformer показывает, как получить XML-данные из одной таблицы и вставить эти XML-данные в другую таблицу при помощи SAX и преобразователя. Сначала метод извлекает объект SLQXML из TestTable1. Затем метод создает пустой объект назначения SQLXML при помощи метода класса Connection [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md). Далее метод обновляет объект назначения SQLXML и записывает XML-данные в TestTable2. Наконец, образец кода выполняет проход по строкам данных, содержащимся в результирующем наборе, и используется метод [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) для прочтения XML-данных в TestTable2.

[!code[JDBC#UsingSQLXML1](../../connect/jdbc/codesnippet/Java/sqlxml-data-type-sample_1.java)]

## <a name="see-also"></a>См. также:

[Работа с типами данных (JDBC)](../../connect/jdbc/working-with-data-types-jdbc.md)
