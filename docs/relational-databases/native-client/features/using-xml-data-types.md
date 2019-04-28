---
title: Использование типов данных XML | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- IRowsetChange interface
- IRowsetUpdate interface
- data access [SQL Server Native Client], xml data type
- SQL Server Native Client OLE DB schema rowsets
- PROVIDER_TYPES rowset
- IColumnsInfo interface
- IRowsetFind interface
- IColumnsRowset interface
- PROCEDURE_PARAMETERS rowset
- SQLNCLI, XML
- xml data type [SQL Server], SQL Server Native Client
- SQL Server Native Client, XML
- IRowset interface
- ISequentialStream interface
- ISSCommandWithParameters interface
- SS_XMLSCHEMA rowset
- SQL Server Native Client OLE DB interfaces
- XML [SQL Server], SQL Server Native Client
- COLUMNS rowset
ms.assetid: a7af5b72-c5c2-418d-a636-ae4ac6270ee5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dfbe6f41150e7d437a6ee1df20e62e41b799c8c0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62668840"
---
# <a name="using-xml-data-types"></a>Использование типов данных XML
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  В версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] был введен тип данных **xml**, позволяющий хранить XML-документы и их фрагменты в базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Тип данных **xml** — это встроенный в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных, несколько напоминающий другие встроенные типы данных, такие как **int** и **varchar**. Как и другие встроенные типы данных, тип данных **xml** можно использовать как тип столбца при создании таблицы, как тип переменной, параметра, тип возвращаемого функцией значения, а также в инструкциях CAST и CONVERT.  
  
## <a name="programming-considerations"></a>Замечания по программированию  
 Язык XML может описывать сам себя в том смысле, что он может по желанию включать заголовок XML, описывающий кодировку документа, например:  
  
 `<?xml version="1.0" encoding="windows-1252"?><doc/>`  
  
 Стандарт языка XML описывает, как обработчик XML определяет кодировку, использованную в документе, по первым нескольким байтам документа. Существует возможность, что кодировка, заданная приложением, не совпадет с кодировкой, заданной в документе. Для документов, переданных как связанные параметры, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] обрабатывает XML как двоичные данные, поэтому никаких преобразований не производится, и синтаксический анализатор XML может без проблем использовать кодировку, указанную в документе. Однако для XML-данных, привязанных как WSTR, приложение должно проверить, что документ имеет кодировку Юникод. Возможно, придется загрузить документ в модель DOM, изменить кодировку на Юникод и сериализовать документ. Если этого не сделать, может произойти порча данных, в результате чего образуется недопустимый или испорченный XML-документ.  
  
 Возможен также конфликт, если XML задается в виде литерала. Например, приведенные ниже инструкции являются недопустимыми.  
  
 `INSERT INTO xmltable(xmlcol) VALUES('<?xml version="1.0" encoding="UTF-16"?><doc/>')`  
  
 `INSERT INTO xmltable(xmlcol) VALUES(N'<?xml version="1.0" encoding="UTF-8"?><doc/>')`  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Поставщик OLE DB для собственного клиента SQL Server  
 DBTYPE_XML — новый, специфичный для XML тип данных в поставщике OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Кроме того, к XML-данным можно получить доступ через существующие типы OLE DB: DBTYPE_BYTES, DBTYPE_WSTR, DBTYPE_BSTR, DBTYPE_XML, DBTYPE_STR, DBTYPE_VARIANT и DBTYPE_IUNKNOWN. Данные, хранимые в столбцах типа XML, можно получить из столбца в наборе строк поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в следующих форматах.  
  
-   Текстовая строка.  
  
-   Интерфейс **ISequentialStream**  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента не включает модуль чтения SAX, но **ISequentialStream** можно легко передать объектам SAX и DOM в MSXML.  
  
 **ISequentialStream** следует использовать для получения больших XML-документов. При работе с типами больших значений в XML используются те же технологии, что и для работы с другими типами больших значений. Дополнительные сведения см. в разделе [использование типов больших значений](../../../relational-databases/native-client/features/using-large-value-types.md).  
  
 Приложение может также получать, вставлять и изменять данные, хранящиеся в столбцах типа XML в наборе строк, через обычные интерфейсы, такие как **IRow::GetColumns**, **IRowChange::SetColumns** и **ICommand::Execute**. Аналогичным образом в случае с получением, приложение может передавать текстовую строку или **ISequentialStream** для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента.  
  
> [!NOTE]  
>  Для отправки данных XML в строковом формате через интерфейс **ISequentialStream** нужно получить этот интерфейс **ISequentialStream**, задав DBTYPE_IUNKNOWN и установив в привязке аргумент *pObject*, равный NULL.  
  
 Если полученные XML-данные усечены из-за недостаточного размера буфера потребителя, возвращаемое значение длины может быть равно 0xffffffff — это означает, что длина данных неизвестна. Это согласуется с реализацией в виде типа данных, передаваемого клиенту в потоке без пересылки информации о длине до пересылки самих данных. В некоторых случаях фактическая длина может быть возвращено при помещено в буфер поставщика всего значения, такие как **IRowset::GetData** и где выполняется преобразование данных.  
  
 XML-данные, переданные в SQL Server, сервер обрабатывает как двоичные данные. Таким образом предотвращается преобразование данных, и это позволяет средству синтаксического анализа XML автоматически обнаружить кодировку XML. Это позволяет принимать в качестве входных данных для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более широкий диапазон XML-документов (например, документы в кодировке UTF-8).  
  
 Если входные данные XML привязаны как тип DBTYPE_WSTR, приложение должно убедиться, что данные уже находятся в кодировке Юникод, чтобы предотвратить всякую возможность повреждения данных ненужными преобразованиями.  
  
### <a name="data-bindings-and-coercions"></a>Привязки данных и приведение типов  
 В приведенной ниже таблице перечислены привязки и приведения, происходящие, когда указанный тип данных используется вместе с типом данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **xml**.  
  
|Тип данных|На сервер<br /><br /> **XML**|На сервер<br /><br /> **Не XML**|С сервера<br /><br /> **XML**|С сервера<br /><br /> **Не XML**|  
|---------------|---------------------------|--------------------------------|-----------------------------|----------------------------------|  
|DBTYPE_XML|Передать<sup>6,7</sup>|Ошибка<sup>1</sup>|ОК<sup>11, 6</sup>|Ошибка<sup>8</sup>|  
|DBTYPE_BYTES|Передать<sup>6,7</sup>|Н/Д<sup>2</sup>|ОК <sup>11, 6</sup>|Н/Д <sup>2</sup>|  
|DBTYPE_WSTR|Передать<sup>6,10</sup>|Н/Д <sup>2</sup>|ОК<sup>4, 6, 12</sup>|Н/Д <sup>2</sup>|  
|DBTYPE_BSTR|Передать<sup>6,10</sup>|Н/Д <sup>2</sup>|ОК <sup>3</sup>|Н/Д <sup>2</sup>|  
|DBTYPE_STR|ОК<sup>6, 9, 10</sup>|Н/Д <sup>2</sup>|ОК<sup>5, 6, 12</sup>|Н/Д <sup>2</sup>|  
|DBTYPE_IUNKNOWN|Байтовый поток через интерфейс **ISequentialStream**<sup>7</sup>|Н/Д <sup>2</sup>|Байтовый поток через интерфейс **ISequentialStream**<sup>11</sup>|Н/Д <sup>2</sup>|  
|DBTYPE_VARIANT (VT_UI1 &#124; VT_ARRAY)|Передать<sup>6,7</sup>|Н/Д <sup>2</sup>|Н/Д|Н/Д <sup>2</sup>|  
|DBTYPE_VARIANT (VT_BSTR)|Передать<sup>6,10</sup>|Н/Д <sup>2</sup>|ОК<sup>3</sup>|Н/Д <sup>2</sup>|  
  
 <sup>1</sup>Если вместе с интерфейсом **ICommandWithParameters::SetParameterInfo** указан тип сервера, отличный от DBTYPE_XML, а в качестве типа метода доступа задан DBTYPE_XML, при выполнении инструкции произойдет ошибка (DB_E_ERRORSOCCURRED, состояние параметра будет равно DBSTATUS_E_BADACCESSOR). В противном случае данные будут отправлены на сервер, но сервер вернет ошибку, указывающую, что неявного преобразования из XML в тип данных параметра не существует.  
  
 <sup>2</sup>выходит за рамки этой статьи.  
  
 <sup>3</sup>Формат UTF-16, метка порядка байтов (BOM) отсутствует, кодировка не указана, данные не завершаются нулем.  
  
 <sup>4</sup>Формат UTF-16, метка порядка байтов (BOM) отсутствует, кодировка не указана, данные завершаются нулем.  
  
 <sup>5</sup>Формат многобайтовый, кодировка совпадает с кодовой страницей клиента, данные завершаются нулем. Преобразование из переданной с сервера кодировки Юникод может вызвать повреждение данных, поэтому такую привязку крайне не рекомендуется использовать.  
  
 <sup>6</sup>Может использоваться BY_REF.  
  
 <sup>7</sup>Данные в формате UTF-16 должны начинаться с метки порядка байтов (BOM). Если метка отсутствует, то кодировка может быть неправильно распознана сервером.  
  
 <sup>8</sup>Проверка может происходить во время создания метода доступа или во время получения данных. Значение ошибки — DB_E_ERRORSOCCURRED, для привязки устанавливается состояние DBBINDSTATUS_UNSUPPORTEDCONVERSION.  
  
 <sup>9</sup>Данные преобразуются в кодировку Юникода с помощью клиентской кодовой страницы до отправки данных на сервер. Если кодировка документа не соответствует клиентской кодовой странице, это может вызвать повреждение данных, поэтому такую привязку крайне не рекомендуется использовать.  
  
 <sup>10</sup>Метка порядка байтов (BOM) всегда добавляется к данным, отправляемым на сервер. Если в начале данных уже стоит метка порядка следования байтов, то в начале буфера будет две метки порядка следования байтов. Сервер использует первую метку для распознавания кодировки как UTF-16, а затем отбрасывает ее. Вторая метка порядка следования байтов рассматривается как символ неразрывного пробела нулевой ширины.  
  
 <sup>11</sup>Данные в формате UTF-16, кодировка не указана, метка порядка байтов (BOM) добавляется к данным, полученным с сервера. Если сервер вернул пустую строку, метка порядка байтов все равно будет возвращена приложению. Если длина буфера составляет нечетное число байтов, данные усекаются правильно. Если все значение возвращается по фрагментам данных, их можно объединить для восстановления правильного значения.  
  
 <sup>12</sup>Если длина буфера меньше двух символов — иными словами, не хватает места для нулем — ошибка переполнения.  
  
> [!NOTE]  
>  Для XML-данных со значением NULL не возвращаются никакие данные.  
  
 Согласно стандарту XML, XML-документы в кодировке UTF-16 должны начинаться с метки порядка следования байтов (BOM); в UTF-16 это код символа 0xFEFF. При работе с привязками типов WSTR и BSTR, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента требует и не добавляет метки порядка БАЙТОВ, так как кодировка задана привязкой. При работе с привязками типов BYTES, XML и IUNKNOWN целью является предоставить возможности для наиболее простого взаимодействия с другими обработчиками XML и хранилищами данных. В этом случае в XML с кодировкой UTF-16 нужно включить метку порядка байтов, и приложение может не заботиться о том, какова на самом деле кодировка данных, потому что большинство обработчиков XML (в том числе SQL Server) вычислят кодировку по нескольким первым байтам данных. XML-данные, полученные от [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client с помощью БАЙТОВ, XML или IUNKNOWN привязок всегда закодированы в кодировке UTF-16 с меткой порядка БАЙТОВ и не содержат внедренной декларации кодировки.  
  
 Преобразование данных, выполняемое основными службами OLE DB (**IDataConvert**), неприменимо к типу DBTYPE_XML.  
  
 Проверка производится при отсылке данных на сервер. Проверку с клиентской стороны и изменение кодировки должно проводить приложение. Обрабатывать непосредственно XML-данные не рекомендуется. Для обработки данных лучше использовать функции чтения DOM или SAX.  
  
 Типы DBTYPE_NULL и DBTYPE_EMPTY могут быть привязаны только для входных параметров. Они не могут быть привязаны для выходных параметров или результатов. При привязке входных параметров следует установить состояние DBSTATUS_S_ISNULL или DBSTATUS_S_DEFAULT.  
  
 DBTYPE_XML можно преобразовать в DBTYPE_EMPTY и DBTYPE_NULL, DBTYPE_EMPTY можно преобразовать в DBTYPE_XML, но DBTYPE_NULL нельзя преобразовать в DBTYPE_XML. Это согласуется с DBTYPE_WSTR.  
  
 Привязка DBTYPE_IUNKNOWN поддерживается, как показано в приведенной таблице, но преобразований между типами DBTYPE_XML и DBTYPE_IUNKNOWN не существует. DBTYPE_IUNKNOWN нельзя использовать с DBTYPE_BYREF.  
  
### <a name="ole-db-rowset-additions-and-changes"></a>Добавления и изменения для наборов строк OLE DB  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Собственный клиент добавляет новые значения или изменяет многие из основных наборов строк схемы OLE DB.  
  
#### <a name="the-columns-and-procedureparameters-schema-rowsets"></a>Наборы строк схем COLUMNS и PROCEDURE_PARAMETERS  
 К наборам строк схем COLUMNS и PROCEDURE_PARAMETERS добавлены следующие столбцы.  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|SS_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Имя каталога, в котором определена коллекция схем XML. Значение NULL для столбцов, отличных от XML или нетипизированных XML-столбцов.|  
|SS_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Имя схемы, в которой определена коллекция схем XML. Значение NULL для столбцов, отличных от XML или нетипизированных XML-столбцов.|  
|SS_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Имя коллекции схем XML. Значение NULL для столбцов, отличных от XML или нетипизированных XML-столбцов.|  
  
#### <a name="the-providertypes-schema-rowset"></a>Набор строк схемы PROVIDER_TYPES  
 В наборе строк схемы PROVIDER_TYPES значение параметра COLUMN_SIZE для типа данных **xml** равно 0, а DATA_TYPE равен DBTYPE_XML.  
  
#### <a name="the-ssxmlschema-schema-rowset"></a>Набор строк схемы SS_XMLSCHEMA  
 Для клиентов добавлен новый набор строк схемы SS_XMLSCHEMA для получения информации о схеме XML. Набор строк SS_XMLSCHEMA содержит следующие столбцы.  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Каталог, которому принадлежит коллекция XML.|  
|SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Схема, которой принадлежит коллекция XML.|  
|SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Имя коллекции схем XML для типизированных XML-столбцов, NULL для всех остальных столбцов.|  
|TARGETNAMESPACEURI|DBTYPE_WSTR|Имя целевого пространства имен схемы XML.|  
|SCHEMACONTENT|DBTYPE_WSTR|Содержимое схемы XML.|  
  
 Для каждой схемы XML область действия ограничивается именем каталога, именем схемы, именем коллекции схем и URI-идентификатором целевого пространства имен. Кроме того, задан новый идентификатор GUID с именем DBSCHEMA_XML_COLLECTIONS. Количество ограничений и столбцы с ограничениями для набора строк схемы SS_XMLSCHEMA определены следующим образом.  
  
|GUID|Количество ограничений|Столбцы с ограничениями|  
|----------|----------------------------|------------------------|  
|DBSCHEMA_XML_COLLECTIONS|4|SCHEMACOLLECTION_CATALOGNAME<br /><br /> SCHEMACOLLECTION_SCHEMANAME<br /><br /> SCHEMACOLLECTIONNAME<br /><br /> TARGETNAMESPACEURI|  
  
### <a name="ole-db-property-set-additions-and-changes"></a>Добавления и изменения для наборов свойств OLE DB  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Собственный клиент добавляет новые значения или изменяет многие из основных свойств OLE DB наборов.  
  
#### <a name="the-dbpropsetsqlserverparameter-property-set"></a>Набор свойств DBPROPSET_SQLSERVERPARAMETER  
 Чтобы обеспечить поддержку **xml** тип данных через OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент реализует новый набор свойств DBPROPSET_SQLSERVERPARAMETER, который содержит следующие значения.  
  
|Имя|Тип|Описание|  
|----------|----------|-----------------|  
|SSPROP_PARAM_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Имя каталога (базы данных), где определена коллекция схем XML. Часть идентификатора трехкомпонентного имени SQL.|  
|SSPROP_PARAM_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Имя схемы XML в коллекции схемы XML. Часть идентификатора трехкомпонентного имени SQL.|  
|SSPROP_PARAM_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Имя коллекции схем XML в каталоге, представляющее собой часть трехчастного идентификатора имени SQL.|  
  
#### <a name="the-dbpropsetsqlservercolumn-property-set"></a>Набор свойств DBPROPSET_SQLSERVERCOLUMN  
 Для поддержки создания таблиц в **ITableDefinition** интерфейс, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент добавляет набор свойств dbpropset_sqlservercolumn три новых столбца.  
  
|Имя|Тип|Описание|  
|----------|----------|-----------------|  
|SSPROP_COL_XML_SCHEMACOLLECTION_CATALOGNAME|VT_BSTR|Для типизированных столбцов XML данное свойство содержит строку, представляющую имя каталога, где хранится схема XML. Для других типов столбцов это свойство содержит пустую строку.|  
|SSPROP_COL_XML_SCHEMACOLLECTION_SCHEMANAME|VT_BSTR|Для типизированных столбцов XML данное свойство содержит строку, представляющую имя схемы XML, задающей этот столбец.|  
|SSPROP_COL_XML_SCHEMACOLLECTIONNAME|VT_BSTR|Для типизированных столбцов XML данное свойство содержит строку, представляющую имя коллекции схем XML, определяющей значение.|  
  
 Подобно значениям SSPROP_PARAM, все эти свойства являются необязательными и по умолчанию пусты. SSPROP_COL_XML_SCHEMACOLLECTION_CATALOGNAME и SSPROP_COL_XML_SCHEMACOLLECTION_SCHEMANAME можно задавать только при заданном свойстве SSPROP_COL_XML_SCHEMACOLLECTIONNAME. При передаче данных в формате XML на сервер, если эти значения включены, они будут проверены на существование (допустимость) в текущей базе данных, а экземпляр данных проверяется по схеме. Во всех случаях, чтобы данные были допустимыми, эти столбцы должны быть все одновременно пусты или все одновременно заполнены.  
  
### <a name="ole-db-interface-additions-and-changes"></a>Добавления и изменения для интерфейсов OLE DB  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Собственный клиент добавляет новые значения или изменяет многие из основных интерфейсов OLE DB.  
  
#### <a name="the-isscommandwithparameters-interface"></a>Интерфейс ISSCommandWithParameters  
 Чтобы обеспечить поддержку **xml** тип данных через OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент реализует ряд изменений, включая добавление [ISSCommandWithParameters](../../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) интерфейс. Этот новый интерфейс наследует основной интерфейс OLE DB — **ICommandWithParameters**. Помимо трех методов, наследуемых от **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**, и **SetParameterInfo**; **ISSCommandWithParameters** предоставляет [GetParameterProperties](../../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md) и [SetParameterProperties](../../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) методы, которые используются для обработки конкретного сервера типы данных.  
  
> [!NOTE]  
>  Интерфейс **ISSCommandWithParameters** также задействует возможности новой структуры SSPARAMPROPS.  
  
#### <a name="the-icolumnsrowset-interface"></a>Интерфейс IColumnsRowset  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Собственный клиент добавляет следующие [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-определенные столбцы в наборе строк, возвращенном **IColumnRowset::GetColumnsRowset** метод. Эти столбцы содержат трехчастное имя коллекции схем XML. Для столбцов не в формате XML и нетипизированных столбцов XML все три данных столбца по умолчанию имеют значение NULL.  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Каталог, которому принадлежит коллекция схем XML.<br /><br /> В противном случае — значение NULL.|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Схема, которой принадлежит коллекция схем XML. В противном случае — значение NULL.|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Имя коллекции схем XML для типизированных XML-столбцов, NULL — для всех остальных столбцов.|  
  
#### <a name="the-irowset-interface"></a>Интерфейс IRowset  
 Метод **IRowset::GetData** служит для получения экземпляра XML в столбце XML. В зависимости от привязки, указанной клиентом, экземпляр XML может быть получен в виде типа DBTYPE_BSTR, DBTYPE_WSTR, DBTYPE_VARIANT, DBTYPE_XML, DBTYPE_STR, DBTYPE_BYTES или как интерфейс через DBTYPE_IUNKNOWN. Если потребитель задает тип DBTYPE_BSTR, DBTYPE_WSTR или DBTYPE_VARIANT, поставщик преобразует экземпляр XML в запрошенный пользователем тип и помещает в местонахождение, заданное соответствующей привязкой.  
  
 Если потребитель задает DBTYPE_IUNKNOWN и устанавливает аргумент *pObject* равным NULL или задает для аргумента *pObject* значение IID_ISequentialStream, поставщик возвращает потребителю интерфейс **ISequentialStream**, чтобы потребитель мог получить из столбца данные XML в виде потока. Затем интерфейс **ISequentialStream** возвращает данные XML в виде потока символов в формате Юникода.  
  
 При возврате значения XML, привязанного к DBTYPE_IUNKNOWN, поставщик передает значение размера `sizeof (IUnknown *)`. Следует заметить, что это согласуется с подходом, который используется при передаче привязанного столбца как DBTYPE_IUnknown или DBTYPE_IDISPATCH, а также при передаче в формате DBTYPE_IUNKNOWN/ISequentialStream, когда точный размер столбца установить не удается.  
  
#### <a name="the-irowsetchange-interface"></a>Интерфейс IRowsetChange  
 Потребитель может изменить экземпляр XML в столбце двумя способами. Первый способ использует объект хранилища с интерфейсом **ISequentialStream**, созданный поставщиком. Потребитель может вызвать метод **ISequentialStream::Write** для непосредственного изменения экземпляра XML, возвращенного поставщиком.  
  
 Второй подход использует методы **IRowsetChange::SetData** или **IRowsetChange::InsertRow**. При таком подходе экземпляр XML в буфере потребителя можно задать привязкой типа DBTYPE_BSTR, DBTYPE_WSTR, DBTYPE_VARIANT, DBTYPE_XML или DBTYPE_IUNKNOWN.  
  
 В случае DBTYPE_BSTR, DBTYPE_WSTR или DBTYPE_VARIANT поставщик сохраняет экземпляр XML из буфера потребителя в соответствующий столбец.  
  
 В случае DBTYPE_IUNKNOWN/ISequentialStream, если потребитель не задал объект хранилища, потребитель должен создать **ISequentialStream** заранее, привязать XML-документа с объектом и затем передайте этот объект к поставщику через **IRowsetChange::SetData** метод. Потребитель может также создать объект хранилища, установить аргумент pObject равным IID_ISequentialStream, создать объект **ISequentialStream**, а затем передать этот объект **ISequentialStream** в метод **IRowsetChange::SetData**. В обоих случаях поставщик может получить объект XML через объект **ISequentialStream** и вставить в нужный столбец.  
  
#### <a name="the-irowsetupdate-interface"></a>Интерфейс IRowsetUpdate  
 Интерфейс **IRowsetUpdate** предоставляет функциональность отсроченных изменений. Данные становятся доступными для наборов строк не становятся доступны другим транзакциям пока потребитель не вызовет **IRowsetUpdate: Update** метод.  
  
#### <a name="the-irowsetfind-interface"></a>Интерфейс IRowsetFind  
 Метод **IRowsetFind::FindNextRow** не работает с типом **xml**. При вызове **IRowsetFind::FindNextRow**, если в аргументе *hAccessor* передается столбец типа DBTYPE_XML, будет возвращен результат DB_E_BADBINDINFO. Это происходит независимо от типа столбца, в котором производится поиск данных. Для любого другого типа привязки вызов **FindNextRow** возвращает результат DB_E_BADCOMPAREOP, если столбец, в котором производится поиск данных, имеет тип **xml**.  
  
## <a name="sql-server-native-client-odbc-driver"></a>Драйвер ODBC для собственного клиента SQL Server  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента, некоторые изменения были внесены некоторые функции для поддержки **xml** тип данных.  
  
### <a name="sqlcolattribute"></a>SQLColAttribute  
 [SQLColAttribute](../../../relational-databases/native-client-odbc-api/sqlcolattribute.md) функция имеет три новых идентификатора поля, включая числе SQL_CA_SS_XML_SCHEMACOLLECTION_CATALOG_NAME, SQL_CA_SS_XML_SCHEMACOLLECTION_SCHEMA_NAME и SQL_CA_SS _XML_SCHEMACOLLECTION_NAME.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента sql_ss_length_unlimited для столбцов SQL_DESC_DISPLAY_SIZE и SQL_DESC_LENGTH столбцы.  
  
### <a name="sqlcolumns"></a>SQLColumns  
 [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md) функция имеет три новых столбца: SS_XML_SCHEMACOLLECTION_CATALOG_NAME, SS_XML_SCHEMACOLLECTION_SCHEMA_NAME и SS_XML_SCHEMACOLLECTION_NAME. Существующий столбец TYPE_NAME используется для обозначения имени типа XML, а значение DATA_TYPE для столбца или параметра типа XML равно SQL_SS_XML.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента sql_ss_length_unlimited для значений COLUMN_SIZE и CHAR_OCTET_LENGTH.  
  
### <a name="sqldescribecol"></a>SQLDescribeCol  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента sql_ss_length_unlimited, если размер столбца не может быть определен в [SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md) функции.  
  
### <a name="sqlgettypeinfo"></a>SQLGetTypeInfo  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента sql_ss_length_unlimited как максимальное значение COLUMN_SIZE для **xml** типа данных в [SQLGetTypeInfo](../../../relational-databases/native-client-odbc-api/sqlgettypeinfo.md) функции.  
  
### <a name="sqlprocedurecolumns"></a>SQLProcedureColumns  
 [SQLProcedureColumns](../../../relational-databases/native-client-odbc-api/sqlprocedurecolumns.md) функция имеет же дополнения столбец как **SQLColumns** функции.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента sql_ss_length_unlimited как максимальное значение COLUMN_SIZE для **xml** тип данных.  
  
### <a name="supported-conversions"></a>Поддерживаемые преобразования  
 При преобразовании данных из типа SQL в типы языка C типы SQL_C_WCHAR, SQL_C_BINARY и SQL_C_CHAR могут быть преобразованы в SQL_SS_XML, со следующими оговорками.  
  
-   SQL_C_WCHAR: Формат — UTF-16 без отметки порядка байтов (BOM), завершаются нулем.  
  
-   SQL_C_BINARY: Формат — UTF-16 с не завершаются нулем. Метка порядка байтов (BOM) добавляется к данным, получаемым с сервера. Если сервер вернул пустую строку, метка порядка байтов все равно будет возвращена приложению. Если длина буфера представляет собой нечетное число байтов, данные усекаются правильно. Если все значение возвращается по фрагментам данных, их можно объединить для восстановления правильного значения.  
  
-   SQL_C_CHAR: Формат — многобайтовые символы, закодированные в кодовой странице клиента с нулем. Преобразование из переданной с сервера кодировки UTF-16 может вызвать повреждение данных, поэтому такую привязку крайне не рекомендуется использовать.  
  
 При преобразовании данных из типов языка С в типы SQL типы SQL_C_WCHAR, SQL_C_BINARY и SQL_C_CHAR могут быть преобразованы в SQL_SS_XML, со следующими оговорками.  
  
-   SQL_C_WCHAR: Всегда Спецификации добавляется к данным, посылаемым на сервер. Если в начале данных уже стоит метка порядка следования байтов, то в начале буфера будет две метки порядка следования байтов. Сервер использует первую метку для распознавания кодировки как UTF-16, а затем отбрасывает ее. Вторая метка порядка следования байтов рассматривается как символ неразрывного пробела нулевой ширины.  
  
-   SQL_C_BINARY: Преобразование не выполняется, и данные передаются на сервер «как есть». Данные в формате UTF-16 должны начинаться с метки порядка байтов. Если метка отсутствует, то кодировка может быть неправильно распознана сервером.  
  
-   SQL_C_CHAR: Данные преобразуются в UTF-16 на клиенте и отправляются на сервер, так же, как SQL_C_WCHAR (включая добавление метки порядка БАЙТОВ). Если кодировка XML не совпадает с клиентской кодовой страницей, это может привести к повреждению данных.  
  
 Согласно стандарту XML, XML-документы в кодировке UTF-16 должны начинаться с метки порядка следования байтов (BOM); в UTF-16 это код символа 0xFEFF. При работе с привязками типа SQL_C_BINARY, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента требует и не добавляет метки порядка БАЙТОВ, так как кодировка задана привязкой. Целью является предоставить возможности для наиболее простого взаимодействия с другими обработчиками XML и хранилищами данных. В этом случае в XML с кодировкой UTF-16 нужно включить метку порядка байтов, и приложение может не заботиться о том, какова на самом деле кодировка данных, потому что большинство обработчиков XML (в том числе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) выяснят кодировку по нескольким первым байтам данных. XML-данные, полученные от [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client с помощью SQL_C_BINARY привязок, всегда закодированы в кодировке UTF-16 с меткой порядка БАЙТОВ и не содержат внедренной декларации кодировки.  
  
## <a name="see-also"></a>См. также  
 [Компоненты собственного клиента SQL Server](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
