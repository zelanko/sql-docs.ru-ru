---
title: Свойства ADO | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- properties [ADO]
- ADO properties
ms.assetid: 0ac0d1a7-6c7a-4f4c-b115-428935e0f98b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: faf6f2c0bee80ae3f8b59a9b8241226facc89edb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="ado-properties"></a>Свойства ADO
|||  
|-|-|  
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|Указывает, на какой странице находится текущая запись.|  
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|Указывает порядковый номер текущей записи **записей** объекта.|  
|[ActiveCommand](../../../ado/reference/ado-api/activecommand-property-ado.md)|Указывает **команда** объекта, который создан связанный **записей** объекта.|  
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|Указывает, к которому **подключения** указанного объекта **команда**, **записей**, или **записи** принадлежит объект.|  
|[ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md)|Указывает фактическую длину значения поля.|  
|[Атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md)|Указывает один или несколько характеристик объекта.|  
|[BOF и конца файла](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|**BOF** указывает, что положение текущей записи перед первой записью в объекте набора записей.<br /><br /> **EOF** указывает, что положение текущей записи после последней записи в объект набора записей.|  
|[Закладка](../../../ado/reference/ado-api/bookmark-property-ado.md)|Указывает закладка, которая однозначно определяет текущую запись в **записей** объекта или задает текущую запись **записей** объект для записи, определяемый допустимую закладку.|  
|[cacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|Указывает количество записей из **записей** объекта, которые локально кэшируются в памяти.|  
|[Глава](../../../ado/reference/ado-api/chapter-property-ado.md)|Возвращает или задает поставщика OLE DB **главе** объекта из/в **ADORecordsetConstruction** объекта.|  
|[Набор символов](../../../ado/reference/ado-api/charset-property-ado.md)|Указывает кодировку, в которой содержимое текстового **поток** должны преобразовываться.|  
|[CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md)|Указывает поток, используемый в качестве входного для **команда** объекта.|  
|[commandText](../../../ado/reference/ado-api/commandtext-property-ado.md)|Показывает, что текст команды должна быть выдан для поставщика.|  
|[CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md)|Указывает время ожидания при выполнении команды перед прекращением попытки и созданием ошибки.|  
|[CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)|Указывает тип **команда** объекта.|  
|[Свойство ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)|Указывает сведения, используемые для установления соединения с источником данных.|  
|[ConnectionTimeout](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)|Указывает время ожидания при установлении подключения, по истечении которого попытка завершается и создается ошибка.|  
|[Count](../../../ado/reference/ado-api/count-property-ado.md)|Указывает количество объектов в коллекции.|  
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|Указывает расположение службы курсора.|  
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|Указывает тип курсора, используемого в **записей** объекта.|  
|[DataMember](../../../ado/reference/ado-api/datamember-property.md)|Указывает имя элемента данных, которые будут извлечены из объекта, на который указывает **DataSource** свойство.|  
|[Источник данных](../../../ado/reference/ado-api/datasource-property-ado.md)|Указывает объект, содержащий данные для представления в виде **записей** объекта.|  
|[DefaultDatabase](../../../ado/reference/ado-api/defaultdatabase-property.md)|Указывает базу данных по умолчанию для **подключения** объекта.|  
|[DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)|Показывает объем данных **поле** объекта.|  
|[Description](../../../ado/reference/ado-api/description-property.md)|Описывает **ошибка** объекта.|  
|[Диалект](../../../ado/reference/ado-api/dialect-property.md)|Указывает, синтаксис и общие правила, поставщик будет использовать для синтаксического анализа **CommandText** или **CommandStream** свойства.|  
|[Направление](../../../ado/reference/ado-api/direction-property.md)|Указывает, является ли **параметр** представляет входным параметром, выходным параметром или оба, или если параметр имеет значение, возвращаемое хранимой процедуры.|  
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|Указывает состояние редактирования текущей записи.|  
|[ЭЛЕКТРИЧЕСКОЙ ПЕРЕГРУЗКИ](../../../ado/reference/ado-api/eos-property.md)|Указывает, является ли текущая позиция в конце потока.|  
|[Фильтр](../../../ado/reference/ado-api/filter-property.md)|Указывает фильтр для данных в **записей**.|  
|[HelpContext и файл справки](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)|Указывает файл справки и раздел, связанный с **ошибка** объекта.<br /><br /> **Идентификатор справки** возвращает идентификатор контекста, в виде **длинные** значение для раздела в файле справки.<br /><br /> **HelpFile** возвращает **строка** значение, результатом которого является полностью разрешенной путь к файлу справки.|  
|[Index](../../../ado/reference/ado-api/index-property.md)|Указывает имя индекса в настоящее время действует для **записей** объекта.|  
|[IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md)|Указывает уровень изоляции для **подключения** объекта.|  
|[Элемент](../../../ado/reference/ado-api/item-property-ado.md)|Указывает конкретный элемент коллекции по имени или порядковый номер.|  
|[LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)|Указывает двоичный символ для использования в качестве разделителя строк в тексте **поток** объектов.|  
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|Указывает тип блокировки записей во время редактирования.|  
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|Указывает, какие записи должны маршалироваться обратно на сервер.|  
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|Указывает максимальное число записей, чтобы вернуться к **записей** из запроса.|  
|[Режим](../../../ado/reference/ado-api/mode-property-ado.md)|Указывает имеющиеся права на изменение данных в **подключения**, **запись**, или **поток** объекта.|  
|[Название](../../../ado/reference/ado-api/name-property-ado.md)|Указывает имя объекта.|  
|[NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md)|Указывает код ошибки поставщика для какого-либо **ошибка** объекта.|  
|[Номер](../../../ado/reference/ado-api/number-property-ado.md)|Указывает число, которое однозначно определяет **ошибка** объекта.|  
|[NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md)|Указывает шкалу числовых значений в **параметр** или **поле** объекта.|  
|[originalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md)|Указывает значение **поле** , состоянии, предшествующем в записи были сделаны изменения.|  
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|Показывает, сколько страниц данных **записей** содержит объект.|  
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|Указывает, сколько записей представляют одну страницу в **записей**.|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|Задает контейнер OLE DB **строки** объекта на **ADORecordConstruction** объекта, чтобы родительские строки преобразуются в ADO **записи** объекта.|  
|[ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)|Указывает строку абсолютный URL-адрес, указывающий на родительский **запись** текущего **записи** объекта.|  
|[Положение](../../../ado/reference/ado-api/position-property-ado.md)|Указывает текущую позицию внутри **поток** объекта.|  
|[Точность](../../../ado/reference/ado-api/precision-property-ado.md)|Указывает степень точность для числовых значений в **параметр** объекта или для числовых **поле** объектов.|  
|[Подготовить](../../../ado/reference/ado-api/prepared-property-ado.md)|Указывает, следует ли сохранять скомпилированную версию перед выполнением команды.|  
|[Поставщик](../../../ado/reference/ado-api/provider-property-ado.md)|Указывает имя поставщика для **подключения** объекта.|  
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|Указывает количество записей в **записей** объекта.|  
|[Типом записи](../../../ado/reference/ado-api/recordtype-property-ado.md)|Указывает тип **записи** объекта.|  
|[Строки](../../../ado/reference/ado-api/row-property-ado.md)|Возвращает или задает поставщика OLE DB **строки** объекта из/в **ADORecordConstruction** объекта.|  
|[RowPosition](../../../ado/reference/ado-api/rowposition-property-ado.md)|Возвращает или задает поставщика OLE DB **RowPosition** объекта из/в **ADORecordsetConstruction** объекта.|  
|[Функции набора строк](../../../ado/reference/ado-api/rowset-property-ado.md)|Возвращает или задает поставщика OLE DB **строк** объекта из/в **ADORecordsetConstruction** объекта.|  
|[Источник (ошибка ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)|Указывает имя объекта или приложения, вызвавшего ошибку.|  
|[Источник (ADO запись)](../../../ado/reference/ado-api/source-property-ado-record.md)|Показывает сущности, представленной **записи** объекта.|  
|[Источник (набора записей ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)|Указывает источник данных в **записей** объекта|  
|[SQLState](../../../ado/reference/ado-api/sqlstate-property.md)|Указывает состояние SQL для конкретного **ошибка** объекта.|  
|[Состояние](../../../ado/reference/ado-api/state-property-ado.md)|Указывает все соответствующие объекты, является ли открытое или закрытое состояние объекта. Указывает, для выполнения асинхронного метода, текущее состояние объекта соединения, выполнение или получение все соответствующие объекты|  
|[Состояние (ADO поле)](../../../ado/reference/ado-api/status-property-ado-field.md)|Указывает состояние **поле** объекта.|  
|[Состояние (набора записей ADO)](../../../ado/reference/ado-api/status-property-ado-recordset.md)|Указывает состояние текущей записи относительно пакетные обновления или другие массовых операций.|  
|[StayInSync](../../../ado/reference/ado-api/stayinsync-property.md)|Указывает в иерархической **записей** объекта, является ли ссылку на основные дочерние записи (т. е *главе*) изменяется при изменения позиции родительской строки.|  
|[Свойство Stream](../../../ado/reference/ado-api/stream-property.md)|Возвращает или задает поставщика OLE DB **поток** объекта из/в **ADOStreamConstruction** объекта.|  
|[Тип](../../../ado/reference/ado-api/type-property-ado.md)|Тип рабочей тип или данные **параметр**, **поле**, или **свойство** объекта.|  
|[Тип (поток ADO)](../../../ado/reference/ado-api/type-property-ado-stream.md)|Указывает тип данных, содержащихся в **поток** (двоичный файл или текст).|  
|[UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)|Показывает текущее значение в базе данных для **поле** объекта.|  
|[Value](../../../ado/reference/ado-api/value-property-ado.md)|Указывает значение, присваиваемое **поле**, **параметр**, или **свойство** объекта.|  
|[Версия](../../../ado/reference/ado-api/version-property-ado.md)|Указывает номер версии ADO.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO коллекций](../../../ado/reference/ado-api/ado-collections.md)   
 [Динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO перечисляемые константы](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Приложение б. ошибки ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [События ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Методы ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Объекты и интерфейсы ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)
