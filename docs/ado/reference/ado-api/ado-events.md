---
title: События ADO | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO]
- ADO, events
ms.assetid: 0ded5ad9-8f83-4224-95af-38512783b972
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 764e47be93509356de38fc90b7b67a1c85e7ff00
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35275523"
---
# <a name="ado-events"></a>События ADO
|||  
|-|-|  
|[BeginTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Вызывается после **BeginTrans** операции.|  
|[CommitTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Вызывается после **CommitTrans** операции.|  
|[ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|Вызывается после начала подключения.|  
|[Отключить](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|Вызывается после завершения соединения.|  
|[EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|Вызывается, когда попытка переместить строку за пределами **записей**.|  
|[ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)|Вызывается после завершения выполнения команды.|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|Вызывается после получения всех записей в длительных асинхронных операций в **записей**.|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|Вызывается периодически во время продолжительной операции асинхронного сообщить, сколько строк в настоящее время выбранный в **записей**.|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Вызывается после изменения значения одного или нескольких **поле** объектов был изменен.|  
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|Вызывается при каждом возникновении предупреждения во время **ConnectionEvent** операции.|  
|[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Вызывается после текущей позиции в **записей** изменения.|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Вызывается после изменения один или несколько записей.|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Вызывается после **записей** изменилось.|  
|[RollbackTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Вызывается после **RollbackTrans** операции.|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Вызывается перед ожидающая выполнения операция изменяет значение одного или нескольких **поле** объекты в **записей**.|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Вызывается до одной или нескольких записей (строк) **записей** изменения.|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Вызывается перед ожидающая выполнения операция изменяет **записей**.|  
|[WillConnect](../../../ado/reference/ado-api/willconnect-event-ado.md)|Вызывается до начала соединения.|  
|[WillExecute](../../../ado/reference/ado-api/willexecute-event-ado.md)|Вызывается непосредственно перед ожидания выполнения команды выполняется по этому соединению и дает пользователю возможность проверки и изменения параметров ожидается выполнение.|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|**WillMove** событие вызвано *перед* ожидающая выполнения операция изменяет текущую позицию в **записей**.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO коллекций](../../../ado/reference/ado-api/ado-collections.md)   
 [Динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO перечисляемые константы](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Приложение б. ошибки ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Обработка событий ADO](../../../ado/guide/data/handling-ado-events.md)   
 [Методы ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Объекты ADO и интерфейсы](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Свойства ADO](../../../ado/reference/ado-api/ado-properties.md)
