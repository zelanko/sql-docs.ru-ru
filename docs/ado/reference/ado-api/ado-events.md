---
title: События ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO]
- ADO, events
ms.assetid: 0ded5ad9-8f83-4224-95af-38512783b972
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 28c64bbe66da1adf6ad4d3a0f9484789ee2a71dd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47838234"
---
# <a name="ado-events"></a>События ADO
|||  
|-|-|  
|[BeginTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Вызывается после **BeginTrans** операции.|  
|[CommitTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Вызывается после **CommitTrans** операции.|  
|[ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|Вызывается после начала соединения.|  
|[Отключить](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|Вызывается после завершения соединения.|  
|[EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|Вызывается при попытке перейти к строке после конца **записей**.|  
|[ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)|Вызывается после завершения выполнения команды.|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|Вызывается после получения всех записей в длительных асинхронных операций в **записей**.|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|Вызывается периодически во время длительной операции асинхронного сообщить, сколько строк в настоящее время были извлечены в **записей**.|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Вызывается после значения из одного или нескольких **поле** объектов был изменен.|  
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|Вызывается при каждом возникновении предупреждения во время **ConnectionEvent** операции.|  
|[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Вызывается после текущей позиции в **записей** изменения.|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Вызывается после изменения один или несколько записей.|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Вызывается после **записей** был изменен.|  
|[RollbackTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Вызывается после **RollbackTrans** операции.|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Вызывается перед отложенная операция изменяет значение одного или нескольких **поле** объекты в **записей**.|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Вызывается перед одну или несколько записей (строк) **записей** изменить.|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Вызывается перед отложенная операция изменяет **записей**.|  
|[WillConnect](../../../ado/reference/ado-api/willconnect-event-ado.md)|Вызывается перед началом подключения.|  
|[WillExecute](../../../ado/reference/ado-api/willexecute-event-ado.md)|Вызывается непосредственно перед ожидания выполнения команды выполняет по этому соединению и дает пользователю возможность проверять и изменять параметры ожидающих выполнения.|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|**События WillMove** событие, называется *перед* отложенная операция изменяет текущую позицию в **записей**.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Коллекции ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Перечисляемые константы ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Приложение б. ошибки объектов ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Обработка событий ADO](../../../ado/guide/data/handling-ado-events.md)   
 [Методы ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Объекты и интерфейсы ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Свойства ADO](../../../ado/reference/ado-api/ado-properties.md)
