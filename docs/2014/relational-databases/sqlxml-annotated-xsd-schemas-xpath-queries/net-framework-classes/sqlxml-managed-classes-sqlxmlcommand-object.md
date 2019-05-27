---
title: Объект SqlXmlCommand (управляемые классы SQLXML) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void ExecuteNonQuery() method
- namespaces property
- Stream ExecuteStream() method
- CommandType property
- RootTag property
- OutputEncoding property
- XmlReader ExecuteXmlReader() method
- Managed Classes [SQLXML], SqlXmlCommand object
- SQLXML Managed Classes, SqlXmlCommand object
- Base Path property
- void ClearParameters() method
- public void ExecuteToStream(Stream outputStream) method
- SqlXmlCommand object
- CommandText property
- XslPath property
- SchemaPath property
- SqlXmlParameter CreateParameter() method
- ClientSideXML property
- CommandStream property
ms.assetid: c1f9e0bb-a89d-4d6a-a96e-289ef516a3a6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d002208a83b58a4c8547bc6ce85db073ced70974
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2019
ms.locfileid: "66010738"
---
# <a name="sqlxmlcommand-object-sqlxml-managed-classes"></a>Объект SqlXmlCommand (управляемые классы SQLXML)
  Этот конструктор используется для объект SqlXmlCommand:  
  
```  
public SqlXmlCommand(string cnString)  
```  
  
 Где `cnString` является строка подключения ADO или OLEDB, определяющий сервер, базу данных и данные входа — например, `Provider=SQLOLEDB; Server=(local); database=AdventureWorks; Integrated Security=SSPI"`.  
  
 В строке соединения параметр `Provider` должен иметь значение SQLOLEDB, а параметр `Data Provider` в строку поставщика не включается).  
  
 Работающий пример см. в разделе [выполнение запросов SQL &#40;управляемых классов SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
## <a name="methods"></a>Методы  
 TheSqlXmlCommand объект поддерживает несколько методов, включая следующие методы для выполнения команды:  
  
 void ExecuteNonQuery()  
 Выполняет команду, но не возвращает никакого результата. Этот метод полезен для выполнения команд, которые не являются запросами (то есть команд, которые ничего не возвращают). Например, выполнение диаграммы обновления или дельты, которая изменяет записи, но ничего не возвращает.  
  
 Stream ExecuteStream()  
 Возвращает новый объект Stream. Этот метод полезен, если нужно вернуть результаты запроса в новом потоке. Работающий пример см. в разделе [выполнение запросов SQL &#40;управляемых классов SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 открытый void ExecuteToStream (Stream outputStream)  
 Записывает результаты запроса в существующий поток. Этот метод полезен в тех случаях, когда у вас есть поток, к которому нужно добавить (например, результаты запроса, записываемый System.Web.HttpResponse.OutputStream) результаты. Работающий пример см. в разделе [выполнение запросов SQL &#40;управляемых классов SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 XmlReader ExecuteXmlReader()  
 Возвращает объект XmlReader. Этот метод можно использовать, чтобы непосредственно манипулировать данными в объекте XmlReader или подключить к цепочкам архитектуры пространства имен System.Xml. Дополнительные сведения см. в документации по платформе [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. Работающий пример см. в разделе [выполнение запросов SQL с использованием метода ExecuteXMLReader](executing-sql-queries-by-using-the-executexmlreader-method.md).  
  
 Объект TheSqlXmlCommand также поддерживает эти дополнительные методы:  
  
 SqlXmlParameter CreateParameter()  
 Создает объект SqlXmlParameter. Можно задать значения для *имя* и *значение* параметров этого объекта. Этот метод полезен для передачи параметров команды. Работающий пример см. в разделе [выполнение запросов SQL &#40;управляемых классов SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 void ClearParameters()  
 Очищает параметры, созданные для данного командного объекта. Это удобно, если нужно выполнить несколько запросов, используя один и тот же командный объект.  
  
## <a name="properties"></a>Свойства  
 Объект SqlXmlCommand также поддерживает следующие свойства:  
  
 ClientSideXml  
 Если для этого свойства задать значение True, преобразование набора строк в XML будет происходить на клиенте, а не на сервере. Это свойство полезно, если нужно переместить вычислительную нагрузку на средний уровень архитектуры. Это свойство также позволяет упаковывать существующие хранимые процедуры в инструкции FOR XML для получения вывода в формате XML.  
  
 SchemaPath  
 Название схемы сопоставления вместе с путем к каталогу (например, C:\x\y\MySchema.xml). Это свойство полезно для задания схемы сопоставления в запросах XPath. Может быть указан абсолютный или относительный путь. Если путь является относительным, базовый путь, указанный в базовый путь используется для определения относительного пути. Если базовый путь не указан, то относительный путь разрешается относительно текущего каталога. Работающий пример см. в разделе [доступ к функциональным возможностям SQLXML в среде .NET](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 XslPath  
 Имя XSL-файла, включая путь к каталогу. Может быть указан абсолютный или относительный путь. Если путь является относительным, базовый путь, указанный в базовый путь используется для определения относительного пути. Если базовый путь не указан, то относительный путь разрешается относительно текущего каталога. Работающий пример см. в разделе [применение преобразования XSL &#40;управляемых классов SQLXML&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).  
  
 Базовый путь  
 Базовый путь (путь к каталогу). Это свойство полезно для разрешения относительного пути, заданного для XSL-файл (с помощью XslPath, свойство), файл схемы сопоставления (с помощью свойства SchemaPath) или ссылка на внешнюю схему в XML-шаблон (указанный с помощью `mapping-schema` атрибут).  
  
 OutputEncoding  
 Указывает кодировку потока, который возвращается при выполнении программы. С помощью этого свойства удобно задавать конкретную кодировку для возвращаемого потока. Примеры распространенных кодировок: UTF-8, ANSI и Unicode. По умолчанию используется UTF-8.  
  
 Пространства имен  
 Разрешает выполнение запросов XPath, использующих пространства имен. Дополнительные сведения о запросах XPath с пространствами имен, см. в разделе [выполнение запросов XPath с пространствами имен &#40;управляемых классов SQLXML&#41;](executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md). Работающий пример см. в разделе [выполнение запросов XPath &#40;управляемых классов SQLXML&#41;](executing-xpath-queries-sqlxml-managed-classes.md).  
  
 RootTag  
 Задает единственный корневой элемент для XML-документа, сформированного при выполнении команды. У допустимого XML-документа может быть только один тег на корневом уровне. Если выполненная команда формирует фрагмент XML (у которого нет единственного элемента верхнего уровня), можно задать корневой элемент для возвращаемого фрагмента XML. Работающий пример см. в разделе [применение преобразования XSL &#40;управляемых классов SQLXML&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).  
  
 CommandText  
 Текст команды. Это свойство используется для задания текста команды, которую нужно выполнить. Работающий пример см. в разделе [выполнение запросов SQL &#40;управляемых классов SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 CommandStream  
 Командный поток. Это свойство служит для выполнения команды из файла (например, XML-шаблона). При использовании CommandStream, только **«Шаблон»**, **«UpdateGram»** и **CommandType «DiffGram»** значения поддерживаются. Работающий пример см. в разделе [выполнение файлов шаблонов с помощью свойства CommandStream](executing-template-files-by-using-the-commandstream-property.md).  
  
 CommandType  
 Идентифицирует тип команды. Это свойство используется для задания типа команды, которую нужно выполнить. Значения в следующей таблице задают тип команды. Работающий пример см. в разделе [доступ к функциональным возможностям SQLXML в среде .NET](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
|Значение|Описание|  
|-----------|-----------------|  
|SqlXmlCommandType.Sql|Выполняет команду SQL (например, `SELECT * FROM Employees FOR XML AUTO`).|  
|SqlXmlCommandType.XPath|Выполняет команду XPath (например, `Employees[@EmployeeID=1]`).|  
|SqlXmlCommandType.Template|Выполняет шаблон XML.|  
|SqlXmlCommandType.TemplateFile|Выполняет файл шаблона, расположенный по указанному пути.|  
|SqlXmlCommandType.UpdateGram|Выполняет диаграмму обновления.|  
|SqlXmlCommandType.Diffgram|Выполняет дельту.|  
  
## <a name="see-also"></a>См. также  
 [Объект SqlXmlParameter &#40;управляемые классы SQLXML&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md)   
 [Объект SqlXmlAdapter &#40;управляемые классы SQLXML&#41;](sqlxml-managed-classes-sqlxmladapter-object.md)  
  
  
