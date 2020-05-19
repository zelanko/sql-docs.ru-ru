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
author: rothja
ms.author: jroth
ms.openlocfilehash: e1b69ced6c5d55b3b393ec30247c1a9f35f9fc57
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747327"
---
# <a name="ado-events"></a>События ADO

|||  
|-|-|  
|[бегинтранскомплете](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Вызывается после операции **примеры BeginTrans** .|  
|[коммиттранскомплете](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Вызывается после операции **CommitTrans** .|  
|[коннекткомплете](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|Вызывается после запуска соединения.|  
|[Соедините](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|Вызывается после завершения соединения.|  
|[ендофрекордсет](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|Вызывается при попытке переместиться в строку после конца **набора записей**.|  
|[ексекутекомплете](../../../ado/reference/ado-api/executecomplete-event-ado.md)|Вызывается после завершения выполнения команды.|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|Вызывается после того, как все записи в длинной асинхронной операции были получены в **набор записей**.|  
|[фетчпрогресс](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|Вызывается периодически во время длительной асинхронной операции, чтобы сообщить, сколько строк в данный момент было извлечено в **набор записей**.|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Вызывается после изменения значения одного или нескольких объектов **полей** .|  
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|Вызывается всякий раз, когда возникает предупреждение во время операции **коннектионевент** .|  
|[мовекомплете](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Вызывается после изменения текущей позицией в **наборе записей** .|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Вызывается после изменения одной или нескольких записей.|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Вызывается после изменения **набора записей** .|  
|[роллбакктранскомплете](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Вызывается после операции **RollbackTrans** .|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Вызывается перед тем, как ожидающая операция изменяет значение одного или нескольких объектов **field** в **наборе записей**.|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Вызывается до того, как одна или несколько записей (строк) изменяются в **наборе записей** .|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Вызывается до того, как ожидающая операция изменяет **набор записей**.|  
|[WillConnect](../../../ado/reference/ado-api/willconnect-event-ado.md)|Вызывается перед началом соединения.|  
|[WillExecute](../../../ado/reference/ado-api/willexecute-event-ado.md)|Вызывается непосредственно перед выполнением ожидающей команды в этом соединении и предоставляет пользователю возможность проверять и изменять параметры выполнения, ожидающие обработки.|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Событие **виллмове** вызывается *до* того, как операция ожидает изменения текущей позицией в **наборе записей**.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Коллекции ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Перечислимые константы ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Приложение б. ошибки ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Обработка событий ADO](../../../ado/guide/data/handling-ado-events.md)   
 [Методы ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Объекты и интерфейсы ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Свойства ADO](../../../ado/reference/ado-api/ado-properties.md)
