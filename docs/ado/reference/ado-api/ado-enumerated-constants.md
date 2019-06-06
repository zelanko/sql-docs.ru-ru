---
title: Перечисляемые константы ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- enumerated constants [ADO]
ms.assetid: c97ed131-1a93-463c-9e61-22f029b0c474
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4d9b2e581bfbce225bd34e78761b9e8ade621172
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66696723"
---
# <a name="ado-enumerated-constants"></a>Перечисляемые константы ADO
Чтобы упростить отладку, ADO перечисления списка значение для каждой константы. Тем не менее это значение исключительно рекомендации и может отличаться от одного выпуска ADO в другой. Ваш код должен основываться только на имя, а не фактическое значение каждого перечислимой константы.  
  
|||  
|-|-|  
|[ADCPROP_ASYNCTHREADPRIORITY_ENUM](../../../ado/reference/ado-api/adcprop-asyncthreadpriority-enum.md)|Для служб удаленных рабочих СТОЛОВ **записей** объекта, задает приоритет выполнения асинхронного потока, который извлекает данные.|  
|[ADCPROP_AUTORECALC_ENUM](../../../ado/reference/ado-api/adcprop-autorecalc-enum.md)|Указывает, когда **MSDataShape** поставщика повторно вычисляет статистические и вычисляемые столбцы в иерархической **записей**.|  
|[ADCPROP_UPDATECRITERIA_ENUM](../../../ado/reference/ado-api/adcprop-updatecriteria-enum.md)|Указывает, какие поля можно использовать для обнаружения конфликтов во время обновления оптимистичного строки источника данных с помощью **записей** объекта.|  
|[ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md)|Указывает ли **UpdateBatch** метод сопровождается неявным **Resync** работы метода и если да, область этой операции.|  
|[AffectEnum](../../../ado/reference/ado-api/affectenum.md)|Указывает, какие записи подвержены операции.|  
|[BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md)|Указывает закладка, показывающая, где должна начинаться операция.|  
|[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)|Указывает, каким образом следует интерпретировать аргумент команды.|  
|[CompareEnum](../../../ado/reference/ado-api/compareenum.md)|Задает относительное положение двух записей, представленный закладок.|  
|[ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md)|Указывает доступные разрешения для изменения данных в **подключения**, откройте **записи**, или заданием значений для **режим** свойство  **Запись** и **Stream** объектов.|  
|[ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md)|Указывает ли **откройте** метод **подключения** должен возвращать объект после (синхронно) или до (асинхронно) подключение будет установлено.|  
|[ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md)|Указывает, следует ли отображать диалоговое окно запрашивать отсутствуют параметры, при открытии соединения с источником данных ODBC.|  
|[CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md)|Задает поведение **CopyRecord** метод.|  
|[CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md)|Указывает расположение в ядре курсора.|  
|[CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)|Указывает, какие функциональные возможности **поддерживает** метод должен проверять на наличие.|  
|[CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md)|Указывает тип курсора, используемого в **записей** объекта.|  
|[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)|Указывает тип данных **поле**, **параметр**, или **свойство**.|  
|[EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md)|Указывает состояние редактирования записи.|  
|[ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md)|Указывает тип ошибки времени выполнения ADO.|  
|[EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md)|Указывает причину, по которой вызвало появление события.|  
|[EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)|Указывает текущее состояние выполнения события.|  
|[ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)|Указывает, как поставщик должен выполнить команду.|  
|[FieldEnum](../../../ado/reference/ado-api/fieldenum.md)|Указывает специальные поля, на которые ссылается **поля** коллекцию **записи** объекта.|  
|[FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md)|Указывает один или несколько атрибутов **поле** объекта.|  
|[FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md)|Указывает состояние **поле** объекта.|  
|[FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)|Указывает группу записей, которые будут отфильтрованы из **записей**.|  
|[GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md)|Указывает, сколько записей следует извлечь из **записей**.|  
|[IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md)|Указывает уровень изоляции транзакции для **подключения** объекта.|  
|[LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md)|Определяет символ, используемый в качестве разделителя строки в тексте **Stream** объектов.|  
|[LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md)|Указывает тип блокировки, уделено записей во время редактирования.|  
|[MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md)|Указывает, какие записи должны быть возвращены на сервер.|  
|[MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md)|Задает поведение **записи** объект **MoveRecord** метод.|  
|[ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)|Указывает, является ли объект открытым или закрытым, подключение к источнику данных, выполнение команды, выборка данных.|  
|[ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md)|Указывает атрибуты **параметр** объекта.|  
|[ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md)|Указывает ли **параметр** представляет входным, выходным или оба, или если параметр является возвращаемым значением из хранимой процедуры.|  
|[PersistFormatEnum](../../../ado/reference/ado-api/persistformatenum.md)|Указывает формат, в котором следует сохранить **записей**.|  
|[PositionEnum](../../../ado/reference/ado-api/positionenum.md)|Задает текущую позицию указателя записи в **записей**.|  
|[PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md)|Указывает атрибуты **свойство** объекта.|  
|[RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md)|Задает для **записи** объект **откройте** метод существующей **записи** должен быть открыт, или новый **записи** должен будет создан.|  
|[RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md)|Указывает параметры для открытия **записи**. Эти значения могут быть объединены с помощью оператора OR.|  
|[RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md)|Указывает состояние записи по отношению к пакетного обновления и других операций массового.|  
|[RecordTypeEnum](../../../ado/reference/ado-api/recordtypeenum.md)|Указывает тип **записи** объекта.|  
|[ResyncEnum](../../../ado/reference/ado-api/resyncenum.md)|Указывает, перезаписываются ли базовые значения путем вызова **Resync**.|  
|[SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md)|Указывает, следует ли создать или перезаписан при сохранении из файла **Stream** объекта. Значения могут объединяться с помощью оператора.|  
|[SchemaEnum](../../../ado/reference/ado-api/schemaenum.md)|Указывает тип схемы **записей** , **OpenSchema** методом. Указывает направление поиска записей в пределах **записей**.|  
|[SearchDirectionEnum](../../../ado/reference/ado-api/searchdirectionenum.md)|Указывает направление поиска записей в пределах **записей**. Указывает тип **Seek** для выполнения.|  
|[SeekEnum](../../../ado/reference/ado-api/seekenum.md)|Указывает тип **Seek** для выполнения. Указывает параметры для открытия **Stream** объекта. Значения могут объединяться с помощью оператора.|  
|[StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md)|Указывает параметры для открытия **Stream** объекта. Значения могут объединяться с помощью оператора. Указывает, следует ли читать весь поток или следующая строка из **Stream** объекта.|  
|[StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)|Указывает, следует ли читать весь поток или следующая строка из **Stream** объекта. Указывает тип данных, хранящихся в **Stream** объекта.|  
|[StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md)|Указывает тип данных, хранящихся в **Stream** объекта. Указывает, добавляется ли разделитель строки в **Stream** объекта.|  
|[StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md)|Указывает, добавляется ли разделитель строки в **Stream** объекта. Задает формат при извлечении **записей** как строка.|  
|[StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md)|Задает формат при извлечении **записей** как строка. Указывает атрибуты транзакции **подключения** объекта.|  
|[XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md)|Указывает атрибуты транзакции **подключения** объекта.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Коллекции ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Приложение б. Ошибки ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [События ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Методы ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Объекты и интерфейсы ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Свойства ADO](../../../ado/reference/ado-api/ado-properties.md)
