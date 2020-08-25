---
description: Перечисляемые константы ADO
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
ms.openlocfilehash: c2b7890cc9926025e7662e8571fb79309590f9de
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776689"
---
# <a name="ado-enumerated-constants"></a>Перечисляемые константы ADO
Для облегчения отладки в перечислениях ADO перечисляются значения для каждой константы. Однако это значение является исключительно рекомендацией и может изменяться от одного выпуска ADO к другому. Код должен зависеть только от имени, а не от фактического значения каждой перечислимой константы.  
  
|Константа|Описание|  
|-|-|  
|[ADCPROP_ASYNCTHREADPRIORITY_ENUM](./adcprop-asyncthreadpriority-enum.md)|Для объекта **RECORDSET** RDS указывает приоритет выполнения асинхронного потока, который получает данные.|  
|[ADCPROP_AUTORECALC_ENUM](./adcprop-autorecalc-enum.md)|Указывает, когда поставщик **мсдаташапе** повторно вычисляет статистические и вычисляемые столбцы в иерархическом **наборе записей**.|  
|[ADCPROP_UPDATECRITERIA_ENUM](./adcprop-updatecriteria-enum.md)|Указывает, какие поля могут использоваться для обнаружения конфликтов во время оптимистического обновления строки источника данных с объектом **Recordset** .|  
|[ADCPROP_UPDATERESYNC_ENUM](./adcprop-updateresync-enum.md)|Указывает, следует ли за методом **UpdateBatch** выполнить неявную операцию повторной **синхронизации** и, если да, область действия этой операции.|  
|[AffectEnum](./affectenum.md)|Указывает, какие записи затрагиваются операцией.|  
|[BookmarkEnum](./bookmarkenum.md)|Задает закладку, которая указывает, где должна начинаться операция.|  
|[CommandTypeEnum](./commandtypeenum.md)|Указывает, как должен интерпретироваться аргумент команды.|  
|[CompareEnum](./compareenum.md)|Задает относительное расположение двух записей, представленных их закладками.|  
|[ConnectModeEnum](./connectmodeenum.md)|Указывает доступные разрешения для изменения данных в **соединении**, открытия **записи**или указания значений для свойства **mode** объектов **Record** и **Stream** .|  
|[ConnectOptionEnum](./connectoptionenum.md)|Указывает, должен ли метод **открытия** объекта **соединения** возвращаться после (синхронно) или перед (асинхронно) установленным соединением.|  
|[ConnectPromptEnum](./connectpromptenum.md)|Указывает, должно ли отображаться диалоговое окно для запроса отсутствующих параметров при открытии соединения с источником данных ODBC.|  
|[CopyRecordOptionsEnum](./copyrecordoptionsenum.md)|Задает поведение метода **копирекорд** .|  
|[CursorLocationEnum](./cursorlocationenum.md)|Задает расположение обработчика курсора.|  
|[CursorOptionEnum](./cursoroptionenum.md)|Указывает, для каких функций должен проверяться метод **поддержки** .|  
|[CursorTypeEnum](./cursortypeenum.md)|Указывает тип курсора, используемого в объекте **набора записей** .|  
|[DataTypeEnum](./datatypeenum.md)|Указывает тип данных **поля**, **параметра**или **Свойства**.|  
|[EditModeEnum](./editmodeenum.md)|Указывает состояние редактирования записи a.|  
|[ErrorValueEnum](./errorvalueenum.md)|Указывает тип ошибки времени выполнения ADO.|  
|[EventReasonEnum](./eventreasonenum.md)|Указывает причину возникновения события.|  
|[EventStatusEnum](./eventstatusenum.md)|Указывает текущее состояние выполнения события.|  
|[ExecuteOptionEnum](./executeoptionenum.md)|Указывает, как поставщик должен выполнять команду.|  
|[FieldEnum](./fieldenum.md)|Задает специальные поля, на которые ссылается коллекция **полей** объекта **Record** .|  
|[FieldAttributeEnum](./fieldattributeenum.md)|Задает один или несколько атрибутов объекта **field** .|  
|[FieldStatusEnum](./fieldstatusenum.md)|Указывает состояние объекта **поля** .|  
|[FilterGroupEnum](./filtergroupenum.md)|Указывает группу записей для фильтрации из **набора записей**.|  
|[GetRowsOptionEnum](./getrowsoptionenum.md)|Указывает, сколько записей необходимо извлечь из **набора записей**.|  
|[IsolationLevelEnum](./isolationlevelenum.md)|Задает уровень изоляции транзакции для объекта **соединения** .|  
|[LineSeparatorsEnum](./lineseparatorsenum.md)|Задает символ, используемый в качестве разделителя строк в объектах текстового **потока** .|  
|[LockTypeEnum](./locktypeenum.md)|Указывает тип блокировки, помещаемой в записи во время редактирования.|  
|[MarshalOptionsEnum](./marshaloptionsenum.md)|Указывает, какие записи должны возвращаться на сервер.|  
|[MoveRecordOptionsEnum](./moverecordoptionsenum.md)|Задает поведение метода **MoveRecord** объекта **записи** .|  
|[ObjectStateEnum](./objectstateenum.md)|Указывает, является ли объект открытым или закрытым, подключением к источнику данных, исполнением команды или извлечением данных.|  
|[ParameterAttributesEnum](./parameterattributesenum.md)|Задает атрибуты объекта **параметра** .|  
|[ParameterDirectionEnum](./parameterdirectionenum.md)|Указывает, представляет ли **параметр** входной параметр, выходной параметр или оба значения, или значение, если параметр является возвращаемым значением хранимой процедуры.|  
|[PersistFormatEnum](./persistformatenum.md)|Задает формат, в котором сохраняется **набор записей**.|  
|[PositionEnum](./positionenum.md)|Задает текущую позиции указателя записи в **наборе записей**.|  
|[PropertyAttributesEnum](./propertyattributesenum.md)|Задает атрибуты объекта **Property** .|  
|[RecordCreateOptionsEnum](./recordcreateoptionsenum.md)|Указывает, следует ли **Открыть существующую запись** в методе **открытия** объекта **Record** или создать новую **запись** .|  
|[RecordOpenOptionsEnum](./recordopenoptionsenum.md)|Задает параметры для открытия **записи**. Эти значения можно комбинировать с помощью оператора или.|  
|[RecordStatusEnum](./recordstatusenum.md)|Указывает состояние записи в отношении обновлений пакетной службы и других небольших операций.|  
|[RecordTypeEnum](./recordtypeenum.md)|Указывает тип объекта **записи** .|  
|[ResyncEnum](./resyncenum.md)|Указывает, перезаписываются ли базовые значения при вызове повторной **синхронизации**.|  
|[SaveOptionsEnum](./saveoptionsenum.md)|Указывает, следует ли создавать или перезаписывать файл при сохранении из объекта **потока** . Значения можно сочетать с оператором AND.|  
|[SchemaEnum](./schemaenum.md)|Указывает тип **набора записей** схемы, извлекаемый методом **OpenSchema** . Указывает направление поиска записей в **наборе записей**.|  
|[SearchDirectionEnum](./searchdirectionenum.md)|Указывает направление поиска записей в **наборе записей**. Указывает тип выполняемого **поиска** .|  
|[SeekEnum](./seekenum.md)|Указывает тип выполняемого **поиска** . Задает параметры для открытия объекта **потока** . Значения можно сочетать с оператором AND.|  
|[StreamOpenOptionsEnum](./streamopenoptionsenum.md)|Задает параметры для открытия объекта **потока** . Значения можно сочетать с оператором AND. Указывает, следует ли считывать весь поток или следующую строку из объекта **потока** .|  
|[StreamReadEnum](./streamreadenum.md)|Указывает, следует ли считывать весь поток или следующую строку из объекта **потока** . Указывает тип данных, хранящихся в объекте **потока** .|  
|[StreamTypeEnum](./streamtypeenum.md)|Указывает тип данных, хранящихся в объекте **потока** . Указывает, добавляется ли разделитель строк к строке, записанной в объект **потока** .|  
|[StreamWriteEnum](./streamwriteenum.md)|Указывает, добавляется ли разделитель строк к строке, записанной в объект **потока** . Задает формат при извлечении **набора записей** в виде строки.|  
|[StringFormatEnum](./stringformatenum.md)|Задает формат при извлечении **набора записей** в виде строки. Задает атрибуты транзакции для объекта **соединения** .|  
|[XactAttributeEnum](./xactattributeenum.md)|Задает атрибуты транзакции для объекта **соединения** .|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO](./ado-api-reference.md)   
 [Коллекции ADO](./ado-collections.md)   
 [Динамические свойства ADO](./ado-dynamic-properties.md)   
 [Приложение б. ошибки ADO](../../guide/appendixes/appendix-b-ado-errors.md)   
 [События ADO](./ado-events.md)   
 [Методы ADO](./ado-methods.md)   
 [Объектная модель ADO](./ado-object-model.md)   
 [Объекты и интерфейсы ADO](./ado-objects-and-interfaces.md)   
 [Свойства ADO](./ado-properties.md)