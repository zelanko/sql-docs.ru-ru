---
description: События ADO
title: События ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: c2925a2c0a25bb919b5cfaae7a6b245f1175b9bb
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88976455"
---
# <a name="ado-events"></a>События ADO

|Событие|Описание|  
|-|-|  
|[бегинтранскомплете](./begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Вызывается после операции **примеры BeginTrans** .|  
|[коммиттранскомплете](./begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Вызывается после операции **CommitTrans** .|  
|[коннекткомплете](./connectcomplete-and-disconnect-events-ado.md)|Вызывается после запуска соединения.|  
|[Соедините](./connectcomplete-and-disconnect-events-ado.md)|Вызывается после завершения соединения.|  
|[ендофрекордсет](./endofrecordset-event-ado.md)|Вызывается при попытке переместиться в строку после конца **набора записей**.|  
|[ексекутекомплете](./executecomplete-event-ado.md)|Вызывается после завершения выполнения команды.|  
|[FetchComplete](./fetchcomplete-event-ado.md)|Вызывается после того, как все записи в длинной асинхронной операции были получены в **набор записей**.|  
|[фетчпрогресс](./fetchprogress-event-ado.md)|Вызывается периодически во время длительной асинхронной операции, чтобы сообщить, сколько строк в данный момент было извлечено в **набор записей**.|  
|[FieldChangeComplete](./willchangefield-and-fieldchangecomplete-events-ado.md)|Вызывается после изменения значения одного или нескольких объектов **полей** .|  
|[InfoMessage](./infomessage-event-ado.md)|Вызывается всякий раз, когда возникает предупреждение во время операции **коннектионевент** .|  
|[мовекомплете](./willmove-and-movecomplete-events-ado.md)|Вызывается после изменения текущей позицией в **наборе записей** .|  
|[RecordChangeComplete](./willchangerecord-and-recordchangecomplete-events-ado.md)|Вызывается после изменения одной или нескольких записей.|  
|[RecordsetChangeComplete](./willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Вызывается после изменения **набора записей** .|  
|[роллбакктранскомплете](./begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Вызывается после операции **RollbackTrans** .|  
|[WillChangeField](./willchangefield-and-fieldchangecomplete-events-ado.md)|Вызывается перед тем, как ожидающая операция изменяет значение одного или нескольких объектов **field** в **наборе записей**.|  
|[WillChangeRecord](./willchangerecord-and-recordchangecomplete-events-ado.md)|Вызывается до того, как одна или несколько записей (строк) изменяются в **наборе записей** .|  
|[WillChangeRecordset](./willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Вызывается до того, как ожидающая операция изменяет **набор записей**.|  
|[WillConnect](./willconnect-event-ado.md)|Вызывается перед началом соединения.|  
|[WillExecute](./willexecute-event-ado.md)|Вызывается непосредственно перед выполнением ожидающей команды в этом соединении и предоставляет пользователю возможность проверять и изменять параметры выполнения, ожидающие обработки.|  
|[WillMove](./willmove-and-movecomplete-events-ado.md)|Событие **виллмове** вызывается *до* того, как операция ожидает изменения текущей позицией в **наборе записей**.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO](./ado-api-reference.md)   
 [Коллекции ADO](./ado-collections.md)   
 [Динамические свойства ADO](./ado-dynamic-properties.md)   
 [Перечислимые константы ADO](./ado-enumerated-constants.md)   
 [Приложение б. ошибки ADO](../../guide/appendixes/appendix-b-ado-errors.md)   
 [Обработка событий ADO](../../guide/data/handling-ado-events.md)   
 [Методы ADO](./ado-methods.md)   
 [Объектная модель ADO](./ado-object-model.md)   
 [Объекты и интерфейсы ADO](./ado-objects-and-interfaces.md)   
 [Свойства ADO](./ado-properties.md)