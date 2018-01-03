---
title: "ADO перечисляемые константы | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: enumerated constants [ADO]
ms.assetid: c97ed131-1a93-463c-9e61-22f029b0c474
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2bbbd8cdea692ed5ed6117ea2e3afc72b90c7b89
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="ado-enumerated-constants"></a>ADO перечисляемые константы
Чтобы упростить отладку, перечислений ADO списка значение для каждой константы. Тем не менее это значение исключительно рекомендации и может меняться от одного выпуска ADO в другой. Код только должны зависеть от имени, а не фактического значения, каждый перечислимой константы.  
  
|||  
|-|-|  
|[ADCPROP_ASYNCTHREADPRIORITY_ENUM](../../../ado/reference/ado-api/adcprop-asyncthreadpriority-enum.md)|Для служб удаленных рабочих СТОЛОВ **записей** объекта, указывающее приоритет выполнения асинхронного потока, который получает данные.|  
|[ADCPROP_AUTORECALC_ENUM](../../../ado/reference/ado-api/adcprop-autorecalc-enum.md)|Указывает, когда **MSDataShape** поставщик повторно вычисляет статистические и вычисляемые столбцы в иерархической **записей**.|  
|[ADCPROP_UPDATECRITERIA_ENUM](../../../ado/reference/ado-api/adcprop-updatecriteria-enum.md)|Указывает, какие поля можно использовать для обнаружения конфликтов во время обновления оптимистичного строки источника данных с **записей** объекта.|  
|[ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md)|Указывает ли **UpdateBatch** метод следуют неявный **Resync** метода операции и если да, область данной операции.|  
|[AffectEnum](../../../ado/reference/ado-api/affectenum.md)|Указывает, какие записи подвержены операции.|  
|[BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md)|Указывает закладка, показывающая, где должен начать операцию.|  
|[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)|Указывает, как следует интерпретировать аргумент команды.|  
|[CompareEnum](../../../ado/reference/ado-api/compareenum.md)|Указывает относительную позицию двух записей, представленный закладок.|  
|[ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md)|Задает разрешения, доступные для изменения данных в **подключения**, откройте **запись**, или указания значения для **режим** свойство  **Запись** и **поток** объектов.|  
|[ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md)|Указывает ли **откройте** метод **подключения** должен возвращать объект после (синхронно) или до (асинхронно) подключения.|  
|[ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md)|Указывает, следует ли отображать диалоговое окно для запроса отсутствуют параметры при открытии соединения с источником данных ODBC.|  
|[CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md)|Задает поведение **CopyRecord** метод.|  
|[CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md)|Указывает расположение в ядре курсора.|  
|[CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)|Указывает, какие функции **поддерживает** метода следует проверить.|  
|[CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md)|Указывает тип курсора, используемого в **записей** объекта.|  
|[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)|Указывает тип данных **поле**, **параметр**, или **свойства**.|  
|[EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md)|Указывает состояние редактирования записи.|  
|[ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md)|Указывает тип ADO ошибок во время выполнения.|  
|[EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md)|Указывает причину, вызвавшего событие.|  
|[EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)|Указывает текущее состояние выполнения события.|  
|[ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)|Указывает, каким образом поставщик должен выполнить команду.|  
|[FieldEnum](../../../ado/reference/ado-api/fieldenum.md)|Указывает специальные поля, на которые ссылается **поля** коллекцию **записи** объекта.|  
|[FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md)|Указывает один или несколько атрибутов **поле** объекта.|  
|[FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md)|Указывает состояние **поле** объекта.|  
|[FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)|Указывает группу записей, которые будут отфильтрованы из **записей**.|  
|[GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md)|Указывает, сколько записей следует извлечь из **записей**.|  
|[IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md)|Задает уровень изоляции транзакции для **подключения** объекта.|  
|[LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md)|Указывает символ, используемый в качестве разделителя строки в тексте **поток** объектов.|  
|[LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md)|Указывает тип блокировка, установленная на записи во время редактирования.|  
|[MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md)|Указывает, какие записи должны быть возвращены на сервер.|  
|[MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md)|Задает поведение **запись** объекта **MoveRecord** метод.|  
|[ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)|Указывает, является ли объект открытым или закрытым, соединение с источником данных, выполнение команды или выборка данных.|  
|[ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md)|Задает атрибуты **параметр** объекта.|  
|[ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md)|Указывает ли **параметр** представляет входным параметром, выходным параметром или оба, или если параметр имеет значение, возвращаемое хранимой процедуры.|  
|[PersistFormatEnum](../../../ado/reference/ado-api/persistformatenum.md)|Указывает формат, в котором следует сохранить **записей**.|  
|[PositionEnum](../../../ado/reference/ado-api/positionenum.md)|Задает текущее положение указателя записи в **записей**.|  
|[PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md)|Задает атрибуты **свойство** объекта.|  
|[RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md)|Указывает для **запись** объекта **откройте** метод существующую **запись** должен быть открыт, или когда новый **записи** должна быть создана.|  
|[RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md)|Задает параметры для открытия **записи**. Эти значения могут объединяться с помощью оператора OR.|  
|[RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md)|Указывает состояние записи по отношению к пакетные обновления и других операций массового.|  
|[RecordTypeEnum](../../../ado/reference/ado-api/recordtypeenum.md)|Указывает тип **записи** объекта.|  
|[ResyncEnum](../../../ado/reference/ado-api/resyncenum.md)|Указывает, перезаписываются ли базовые значения путем вызова **Resync**.|  
|[SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md)|Указывает, следует создать или перезаписан при сохранении из файла **поток** объекта. Значения могут быть объединены с помощью оператора.|  
|[SchemaEnum](../../../ado/reference/ado-api/schemaenum.md)|Указывает тип схемы **записей** , **OpenSchema** извлекает метод. Указывает направление поиска записей в **записей**.|  
|[SearchDirectionEnum](../../../ado/reference/ado-api/searchdirectionenum.md)|Указывает направление поиска записей в **записей**. Указывает тип **Seek** для выполнения.|  
|[SeekEnum](../../../ado/reference/ado-api/seekenum.md)|Указывает тип **Seek** для выполнения. Задает параметры для открытия **поток** объекта. Значения могут быть объединены с помощью оператора.|  
|[StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md)|Задает параметры для открытия **поток** объекта. Значения могут быть объединены с помощью оператора. Указывает, должны ли считываться весь поток или следующую строку из **поток** объекта.|  
|[StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)|Указывает, должны ли считываться весь поток или следующую строку из **поток** объекта. Указывает тип данных, хранящихся в **поток** объекта.|  
|[StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md)|Указывает тип данных, хранящихся в **поток** объекта. Указывает, добавляется ли разделитель строки в **поток** объекта.|  
|[StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md)|Указывает, добавляется ли разделитель строки в **поток** объекта. Указывает формат при извлечении **записей** как строка.|  
|[StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md)|Указывает формат при извлечении **записей** как строка. Задает атрибуты транзакции **подключения** объекта.|  
|[XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md)|Задает атрибуты транзакции **подключения** объекта.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO коллекций](../../../ado/reference/ado-api/ado-collections.md)   
 [Динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Приложение б. ошибки ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [События ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Методы ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Объекты ADO и интерфейсы](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Свойства ADO](../../../ado/reference/ado-api/ado-properties.md)
