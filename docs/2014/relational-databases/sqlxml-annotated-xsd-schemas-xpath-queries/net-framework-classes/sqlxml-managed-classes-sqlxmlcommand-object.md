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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66010738"
---
# <a name="sqlxmlcommand-object-sqlxml-managed-classes"></a>Объект SqlXmlCommand (управляемые классы SQLXML)
  Это конструктор для объекта SqlXmlCommand:  
  
```  
public SqlXmlCommand(string cnString)  
```  
  
 Где `cnString` — строка подключения ADO или OLEDB, идентифицирующая сервер, базу данных и сведения об имени входа, например `Provider=SQLOLEDB; Server=(local); database=AdventureWorks; Integrated Security=SSPI"`.  
  
 В строке соединения параметр `Provider` должен иметь значение SQLOLEDB, а параметр `Data Provider` в строку поставщика не включается).  
  
 Рабочий пример см. в разделе [Выполнение SQL-запросов &#40;управляемых классов SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
## <a name="methods"></a>Методы  
 Объект Сесклксмлкомманд поддерживает несколько методов, включая следующие методы для исполнения команды:  
  
 void ExecuteNonQuery ()  
 Выполняет команду, но не возвращает никакого результата. Этот метод полезен для выполнения команд, которые не являются запросами (то есть команд, которые ничего не возвращают). Например, выполнение диаграммы обновления или дельты, которая изменяет записи, но ничего не возвращает.  
  
 Stream Ексекутестреам ()  
 Возвращает новый объект потока. Этот метод полезен, если нужно вернуть результаты запроса в новом потоке. Рабочий пример см. в разделе [Выполнение SQL-запросов &#40;управляемых классов SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 открытая void Ексекутетостреам (Stream outputStream)  
 Записывает результаты запроса в существующий поток. Этот метод полезен при наличии потока, к которому должны быть добавлены результаты (например, чтобы результаты запроса записывались в System. Web. HttpResponse. OutputStream). Рабочий пример см. в разделе [Выполнение SQL-запросов &#40;управляемых классов SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 XmlReader ExecuteXmlReader ()  
 Возвращает объект XmlReader. Этот метод можно использовать для непосредственного управления данными в объекте XmlReader или подключения к связанной архитектуре System. XML. Дополнительные сведения см. в документации по платформе [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. Рабочий пример см. в разделе [Выполнение SQL-запросов с помощью метода ExecuteXMLReader](executing-sql-queries-by-using-the-executexmlreader-method.md).  
  
 Объект Сесклксмлкомманд также поддерживает следующие дополнительные методы:  
  
 SqlXmlParameter CreateParameter ()  
 Создает объект SqlXmlParameter. Можно задать значения для параметров *Name* и *value* этого объекта. Этот метод полезен для передачи параметров команды. Рабочий пример см. в разделе [Выполнение SQL-запросов &#40;управляемых классов SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 void ClearParameters ()  
 Очищает параметры, созданные для данного командного объекта. Это удобно, если нужно выполнить несколько запросов, используя один и тот же командный объект.  
  
## <a name="properties"></a>Свойства  
 Объект SqlXmlCommand также поддерживает следующие свойства:  
  
 клиентсидексмл  
 Если для этого свойства задать значение True, преобразование набора строк в XML будет происходить на клиенте, а не на сервере. Это свойство полезно, если нужно переместить вычислительную нагрузку на средний уровень архитектуры. Это свойство также позволяет упаковывать существующие хранимые процедуры в инструкции FOR XML для получения вывода в формате XML.  
  
 SchemaPath  
 Название схемы сопоставления вместе с путем к каталогу (например, C:\x\y\MySchema.xml). Это свойство полезно для задания схемы сопоставления в запросах XPath. Может быть указан абсолютный или относительный путь. Если путь является относительным, то базовый путь, указанный в качестве базового пути, используется для разрешения относительного пути. Если базовый путь не указан, то относительный путь разрешается относительно текущего каталога. Рабочий пример см. в разделе [доступ к функциям SQLXML в среде .NET](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 ксслпас  
 Имя XSL-файла, включая путь к каталогу. Может быть указан абсолютный или относительный путь. Если путь является относительным, то базовый путь, указанный в качестве базового пути, используется для разрешения относительного пути. Если базовый путь не указан, то относительный путь разрешается относительно текущего каталога. Рабочий пример см. в разделе [применение преобразования XSL &#40;управляемых классов SQLXML&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).  
  
 Базовый путь  
 Базовый путь (путь к каталогу). Это свойство полезно для разрешения относительного пути, указанного для XSL-файла (с помощью свойства Ксслпас), файла схемы сопоставления (с помощью свойства Счемапас) или ссылки на внешнюю схему в XML-шаблоне (указывается с помощью `mapping-schema` атрибута).  
  
 OutputEncoding  
 Указывает кодировку потока, который возвращается при выполнении программы. С помощью этого свойства удобно задавать конкретную кодировку для возвращаемого потока. Примеры распространенных кодировок: UTF-8, ANSI и Unicode. По умолчанию используется UTF-8.  
  
 Пространства имен  
 Разрешает выполнение запросов XPath, использующих пространства имен. Дополнительные сведения о запросах XPath с пространствами имен см. в разделе [исполнение запросов XPath с пространствами имен &#40;управляемые классы SQLXML&#41;](executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md). Рабочий пример см. в разделе [выполнение запросов XPath &#40;управляемых классов SQLXML&#41;](executing-xpath-queries-sqlxml-managed-classes.md).  
  
 руттаг  
 Задает единственный корневой элемент для XML-документа, сформированного при выполнении команды. У допустимого XML-документа может быть только один тег на корневом уровне. Если выполненная команда формирует фрагмент XML (у которого нет единственного элемента верхнего уровня), можно задать корневой элемент для возвращаемого фрагмента XML. Рабочий пример см. в разделе [применение преобразования XSL &#40;управляемых классов SQLXML&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).  
  
 CommandText  
 Текст команды. Это свойство используется для задания текста команды, которую нужно выполнить. Рабочий пример см. в разделе [Выполнение SQL-запросов &#40;управляемых классов SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 CommandStream  
 Командный поток. Это свойство служит для выполнения команды из файла (например, XML-шаблона). При использовании CommandStream поддерживаются только значения CommandType **"Template"**, **"диаграмма обновления"** и **"DiffGram"** . Рабочий пример см. в разделе [выполнение файлов шаблонов с помощью свойства CommandStream](executing-template-files-by-using-the-commandstream-property.md).  
  
 CommandType  
 Идентифицирует тип команды. Это свойство используется для задания типа команды, которую нужно выполнить. Значения в следующей таблице задают тип команды. Рабочий пример см. в разделе [доступ к функциям SQLXML в среде .NET](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
|Значение|Description|  
|-----------|-----------------|  
|Склксмлкоммандтипе. SQL|Выполняет команду SQL (например, `SELECT * FROM Employees FOR XML AUTO`).|  
|Склксмлкоммандтипе. XPath|Выполняет команду XPath (например, `Employees[@EmployeeID=1]`).|  
|Склксмлкоммандтипе. шаблон|Выполняет шаблон XML.|  
|Склксмлкоммандтипе. TemplateFile|Выполняет файл шаблона, расположенный по указанному пути.|  
|Склксмлкоммандтипе. Диаграмма обновления|Выполняет диаграмму обновления.|  
|Склксмлкоммандтипе. DiffGram|Выполняет дельту.|  
  
## <a name="see-also"></a>См. также:  
 [Объект SqlXmlParameter &#40;управляемые классы SQLXML&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md)   
 [Объект Склксмладаптер &#40;управляемые классы SQLXML&#41;](sqlxml-managed-classes-sqlxmladapter-object.md)  
  
  
