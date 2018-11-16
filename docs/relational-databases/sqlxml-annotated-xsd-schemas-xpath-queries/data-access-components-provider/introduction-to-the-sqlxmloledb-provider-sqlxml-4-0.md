---
title: Введение в поставщик SQLXMLOLEDB (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, properties
- adExecuteStream flag
- SQLXMLOLEDB Provider, about SQLXMLOLEDB Provider
ms.assetid: 2e3f3817-4209-4bf4-9f46-248c95bc6f1b
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8d62031bdd9614cb4dafb8c7c8e18bf9e3b90cb8
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51657823"
---
# <a name="introduction-to-the-sqlxmloledb-provider-sqlxml-40"></a>Введение в поставщик SQLXMLOLEDB (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Поставщик SQLXMLOLEDB — это поставщик OLE DB, который предоставляет функциональность [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML через объекты ADO. Однако этот поставщик может выполнять команды только в режиме ADO «запись в выходящий поток». Поставщик SQLXMLOLEDB не является поставщиком набора строк. При выполнении команды, необходимо указать adExecuteStream, флаг, который указывает объектам ADO использовать выходной поток, который вы указали.  
  
 В примере показан синтаксис для команды Execute, в котором указывается adExecuteStream, флаг:  
  
```  
Dim oTestCommand As New ADODB.Command  
...  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Execute , , adExecuteStream  
...  
```  
  
## <a name="sqlxmloledb-provider-specific-properties"></a>Свойства поставщика SQLXMLOLEDB  
 Поставщик SQLXMLOLEDB имеет следующие характерные для него свойства соединения.  
  
|Соединение<br /><br /> свойство|По умолчанию<br /><br /> (если есть)|Описание|  
|-----------------------------|----------------------------|-----------------|  
|Поставщик данных||Предоставляет идентификатор PROGID поставщика OLE DB, через который SQLXMLOLEDB выполняет команды. Начиная с SQLXML 4.0 и [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], этот поставщик является частью собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; поэтому значение этого свойства может быть только «SQLNCLI11». Дополнительные сведения см. в статье [Программирование SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md).|  
  
 Поставщик SQLXMLOLEDB имеет следующие характерные для него свойства команды.  
  
|Command<br /><br /> свойство|По умолчанию<br /><br /> (если есть)|Описание|  
|--------------------------|----------------------------|-----------------|  
|Базовый путь|""|Указывает базовый путь к файлу. Базовый путь к файлу используется для указания местоположения файлов языка XSL или схемы сопоставления. Базовый путь файла также используется для разрешения относительных путей к XSL или сопоставления файлов схемы, которые были указаны в свойствах XSL или схемы сопоставления.<br /><br /> Пример, в котором используется это свойство, см. в разделе [выполнение запросов XPath &#40;поставщик SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-sqlxmloledb-provider.md).|  
|ClientSideXML|False|Если требуется, чтобы процесс преобразования набора строк в XML был выполнен на клиенте, а не на сервере, установите этому свойству значение TRUE. Это полезно, когда необходимо переместить нагрузку производительности на средний уровень.<br /><br /> Пример, в котором используется это свойство, см. в разделе [выполнение запросов SQL &#40;поставщик SQLXMLOLEDB&#41; ](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-sql-queries-sqlxmloledb-provider.md) или [выполнение шаблонов, содержащих SQL-запросы &#40;поставщик SQLXMLOLEDB&#41; ](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md).|  
|Тип содержимого||Возвращает тип выходящего содержимого. Это свойство доступно только для чтения.<br /><br /> Это свойство предоставляет браузеру сведения о типе содержимого (например, ТЕКСТ/XML, ТЕКСТ/HTML, изображение/jpeg и так далее). Значение этого свойства становится **тип содержимого** поле, которое отправляется в браузер как часть заголовка HTTP, содержащего тип MIME (Multipurpose Internet Mail Extensions) отправляется в качестве текста документа.|  
|Схема сопоставления|NULL|Когда клиентское приложение выполняет запрос XPath к схеме сопоставления (XDR или XSD), это свойство используется для указания имени схемы сопоставления.<br /><br /> Указываемый путь может быть относительным (xyz/abc/МояСхема.xml) или абсолютным (C:\МояПапка\abc\МояСхема.xml).<br /><br /> Если указан относительный путь, базовый путь, указанный в свойстве базовый путь используется для определения относительного пути. Если путь не был указан в свойстве базовый путь, относительный путь задается относительно текущего каталога.<br /><br /> При указании значения для свойства схемы сопоставления, можно указать путь к локальному каталогу или URL-адрес (https://). В случае указания URL-адреса необходимо настроить модуль WinHTTP для доступа к серверам HTTP и HTTPS через прокси-сервер. Сделать это можно при помощи программы Proxycfg.exe. Дополнительные сведения см. в статье «Использование программы настройки доступа модуля WinHTTP через прокси-сервер» в библиотеке MSDN.<br /><br /> Пример, в котором используется это свойство, см. в разделе [выполнение запросов XPath &#40;поставщик SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-sqlxmloledb-provider.md).|  
|пространства имен||Это свойство включает использование запросов XPath, которые используют пространства имен. Пример, в котором используется это свойство, см. в разделе [выполнение запросов XPath с пространствами имен &#40;поставщик SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md).|  
|ss Stream Flags||Это свойство используется для указания конкретных типов ограничений безопасности. Например, может потребоваться запретить URL-ссылки на файлы или абсолютные пути к файлам (например, внешние веб-сайты). Либо может потребоваться запретить запросы в шаблонах.<br /><br /> Свойству могут быть присвоены следующие значения:<br /><br /> 1 = STREAM_FLAGS_DISALLOW_URL 2 = STREAM_FLAGS_DISALLOW_ABSOLUTE_PATH 4 = STREAM_FLAGS_DISALLOW_QUERY 8 = STREAM_FLAGS_ DONTCACHEMAPPINGSCHEMA 16 = STREAM_FLAGS_DONTCACHETEMPLATE 32 = STREAM_FLAGS_DONTCACHEXSL<br /><br /> Дополнительные сведения об этих значениях приведены в следующей таблице.|  
|xml root||Это свойство используется для определения корневого тега для итогового XML. Например, в случае выполнения запросов SQL к базе данных и отсутствия в итоговом XML-документе одного корневого элемента, значение этого свойства используется для добавления одного корневого элемента в документ.<br /><br /> Пример, в котором используется это свойство, см. в разделе [выполнение запросов SQL &#40;поставщик SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-sql-queries-sqlxmloledb-provider.md).|  
|xsl||Это свойство используется для указания имени файла XSL, когда требуется применить преобразование XSL к XML-документу, возвращенному запросом.<br /><br /> Указываемый путь может быть относительным (xyz/abc/МойXSL.xsl) или абсолютным (C:\МояПапка\abc\МойXSL.xsl).<br /><br /> Если указан относительный путь, базовый путь, указанный в свойстве базовый путь используется для определения относительного пути. Если путь не был указан в свойстве базовый путь, относительный путь задается относительно текущего каталога.<br /><br /> Пример, в котором используется это свойство см. в разделе Применение преобразования XSL (поставщик SQLXMLOLEDB).|  
  
 Следующая таблица содержит описания ss Stream флаги значения свойств.  
  
|Значение свойства|Описание|  
|--------------------|-----------------|  
|STREAM_FLAGS_DISALLOW_URL|URL-адреса не принимаются для схем сопоставления или XSL.|  
|STREAM_FLAGS_DISALLOW_ABSOLTE_PATH|Путь, указываемый для схемы сопоставления или XSL, должен задаваться относительно базового пути самого шаблона.|  
|STREAM_FLAGS_DISALLOW_QUERY|Запросы недопустимы в шаблоне.|  
|STREAM_FLAGS_DONTCACHEMAPPINGSCHEMA|Схема сопоставления не кэшируется. Значение этого свойства полезно на стадии разработки базы данных, когда схемы базы данных часто изменяются.|  
|STREAM_FLAGS_DONTCACHETEMPLATE|Шаблоны не кэшируются.|  
|STREAM_FLAGS_DONTCACHEXSL|XSL не кэшируется.|  
  
  
