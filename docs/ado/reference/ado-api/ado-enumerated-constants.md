---
title: Перечислимые константы ADO | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 74d3cc347d14a1d02ae5953b7762513b252493e6
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242884"
---
# <a name="ado-enumerated-constants"></a>Перечисляемые константы ADO
Для облегчения отладки в перечислениях ADO перечисляются значения для каждой константы. Однако это значение является исключительно рекомендацией и может изменяться от одного выпуска ADO к другому. Код должен зависеть только от имени, а не от фактического значения каждой перечислимой константы.  
  
|Константа|Описание|  
|-|-|  
|[ADCPROP_ASYNCTHREADPRIORITY_ENUM](../../../ado/reference/ado-api/adcprop-asyncthreadpriority-enum.md)|Для объекта **RECORDSET** RDS указывает приоритет выполнения асинхронного потока, который получает данные.|  
|[ADCPROP_AUTORECALC_ENUM](../../../ado/reference/ado-api/adcprop-autorecalc-enum.md)|Указывает, когда поставщик **мсдаташапе** повторно вычисляет статистические и вычисляемые столбцы в иерархическом **наборе записей**.|  
|[ADCPROP_UPDATECRITERIA_ENUM](../../../ado/reference/ado-api/adcprop-updatecriteria-enum.md)|Указывает, какие поля могут использоваться для обнаружения конфликтов во время оптимистического обновления строки источника данных с объектом **Recordset** .|  
|[ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md)|Указывает, следует ли за методом **UpdateBatch** выполнить неявную операцию повторной **синхронизации** и, если да, область действия этой операции.|  
|[AffectEnum](../../../ado/reference/ado-api/affectenum.md)|Указывает, какие записи затрагиваются операцией.|  
|[BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md)|Задает закладку, которая указывает, где должна начинаться операция.|  
|[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)|Указывает, как должен интерпретироваться аргумент команды.|  
|[CompareEnum](../../../ado/reference/ado-api/compareenum.md)|Задает относительное расположение двух записей, представленных их закладками.|  
|[ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md)|Указывает доступные разрешения для изменения данных в **соединении**, открытия **записи**или указания значений для свойства **mode** объектов **Record** и **Stream** .|  
|[ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md)|Указывает, должен ли метод **открытия** объекта **соединения** возвращаться после (синхронно) или перед (асинхронно) установленным соединением.|  
|[ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md)|Указывает, должно ли отображаться диалоговое окно для запроса отсутствующих параметров при открытии соединения с источником данных ODBC.|  
|[CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md)|Задает поведение метода **копирекорд** .|  
|[CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md)|Задает расположение обработчика курсора.|  
|[CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)|Указывает, для каких функций должен проверяться метод **поддержки** .|  
|[CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md)|Указывает тип курсора, используемого в объекте **набора записей** .|  
|[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)|Указывает тип данных **поля**, **параметра**или **Свойства**.|  
|[EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md)|Указывает состояние редактирования записи a.|  
|[ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md)|Указывает тип ошибки времени выполнения ADO.|  
|[EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md)|Указывает причину возникновения события.|  
|[EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)|Указывает текущее состояние выполнения события.|  
|[ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)|Указывает, как поставщик должен выполнять команду.|  
|[FieldEnum](../../../ado/reference/ado-api/fieldenum.md)|Задает специальные поля, на которые ссылается коллекция **полей** объекта **Record** .|  
|[FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md)|Задает один или несколько атрибутов объекта **field** .|  
|[FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md)|Указывает состояние объекта **поля** .|  
|[FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)|Указывает группу записей для фильтрации из **набора записей**.|  
|[GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md)|Указывает, сколько записей необходимо извлечь из **набора записей**.|  
|[IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md)|Задает уровень изоляции транзакции для объекта **соединения** .|  
|[LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md)|Задает символ, используемый в качестве разделителя строк в объектах текстового **потока** .|  
|[LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md)|Указывает тип блокировки, помещаемой в записи во время редактирования.|  
|[MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md)|Указывает, какие записи должны возвращаться на сервер.|  
|[MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md)|Задает поведение метода **MoveRecord** объекта **записи** .|  
|[ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)|Указывает, является ли объект открытым или закрытым, подключением к источнику данных, исполнением команды или извлечением данных.|  
|[ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md)|Задает атрибуты объекта **параметра** .|  
|[ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md)|Указывает, представляет ли **параметр** входной параметр, выходной параметр или оба значения, или значение, если параметр является возвращаемым значением хранимой процедуры.|  
|[PersistFormatEnum](../../../ado/reference/ado-api/persistformatenum.md)|Задает формат, в котором сохраняется **набор записей**.|  
|[PositionEnum](../../../ado/reference/ado-api/positionenum.md)|Задает текущую позиции указателя записи в **наборе записей**.|  
|[PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md)|Задает атрибуты объекта **Property** .|  
|[RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md)|Указывает, следует ли **Открыть существующую запись** в методе **открытия** объекта **Record** или создать новую **запись** .|  
|[RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md)|Задает параметры для открытия **записи**. Эти значения можно комбинировать с помощью оператора или.|  
|[RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md)|Указывает состояние записи в отношении обновлений пакетной службы и других небольших операций.|  
|[RecordTypeEnum](../../../ado/reference/ado-api/recordtypeenum.md)|Указывает тип объекта **записи** .|  
|[ResyncEnum](../../../ado/reference/ado-api/resyncenum.md)|Указывает, перезаписываются ли базовые значения при вызове повторной **синхронизации**.|  
|[SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md)|Указывает, следует ли создавать или перезаписывать файл при сохранении из объекта **потока** . Значения можно сочетать с оператором AND.|  
|[SchemaEnum](../../../ado/reference/ado-api/schemaenum.md)|Указывает тип **набора записей** схемы, извлекаемый методом **OpenSchema** . Указывает направление поиска записей в **наборе записей**.|  
|[SearchDirectionEnum](../../../ado/reference/ado-api/searchdirectionenum.md)|Указывает направление поиска записей в **наборе записей**. Указывает тип выполняемого **поиска** .|  
|[SeekEnum](../../../ado/reference/ado-api/seekenum.md)|Указывает тип выполняемого **поиска** . Задает параметры для открытия объекта **потока** . Значения можно сочетать с оператором AND.|  
|[StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md)|Задает параметры для открытия объекта **потока** . Значения можно сочетать с оператором AND. Указывает, следует ли считывать весь поток или следующую строку из объекта **потока** .|  
|[StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)|Указывает, следует ли считывать весь поток или следующую строку из объекта **потока** . Указывает тип данных, хранящихся в объекте **потока** .|  
|[StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md)|Указывает тип данных, хранящихся в объекте **потока** . Указывает, добавляется ли разделитель строк к строке, записанной в объект **потока** .|  
|[StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md)|Указывает, добавляется ли разделитель строк к строке, записанной в объект **потока** . Задает формат при извлечении **набора записей** в виде строки.|  
|[StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md)|Задает формат при извлечении **набора записей** в виде строки. Задает атрибуты транзакции для объекта **соединения** .|  
|[XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md)|Задает атрибуты транзакции для объекта **соединения** .|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Коллекции ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Приложение б. ошибки ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [События ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Методы ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Объекты и интерфейсы ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Свойства ADO](../../../ado/reference/ado-api/ado-properties.md)
