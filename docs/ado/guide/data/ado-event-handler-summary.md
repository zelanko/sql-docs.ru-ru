---
title: "Сводка обработчик событий ADO | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [ADO], about event handlers
- event handlers [ADO]
ms.assetid: b34f4472-5e04-4a2c-ab64-38d6eca31a69
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e7a241c21719e2181f8dbbce11742a273d8552d7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="ado-connection-and-recordset-events"></a>Соединение ADO и события набора записей
Два объекта ADO может порождать события: [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта и [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта. **ConnectionEvent** семейства относится к операциям на **подключения** объекта и **RecordsetEvent** семейства относится к операциям на  **Набор записей** объекта.

-   **События подключения**: события выдаются при начинает транзакцию для подключения, фиксируется или откатывается назад; когда [команда](../../../ado/reference/ado-api/command-object-ado.md) выполняет; при возникновении предупреждения во время **событие соединения**операции; или когда **подключения** начинается или заканчивается.

-   **Набор записей событий**: события выдаются вокруг асинхронное извлечение операций, а также при переходе по строкам **набора записей** , следует изменить поле в строке **набора записей**, Измените строку в **записей**откройте **набора записей** серверный курсор, закройте **записей**, или внести изменения никакой в  **Набор записей**.

 В следующей таблице перечислены события и их описания.

|ConnectionEvent|Description|
|---------------------|-----------------|
|[RollbackTransComplete BeginTransComplete CommitTransComplete,](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|**Управление транзакциями** — уведомление о запуске текущей транзакции в соединении, зафиксирована, или удалена.|
|[WillConnect](../../../ado/reference/ado-api/willconnect-event-ado.md), [ConnectComplete, отключение](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|**Управление соединениями** — уведомление, которое будет запускаться текущего соединения, запуска или завершения.|
|[WillExecute](../../../ado/reference/ado-api/willexecute-event-ado.md), [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)|**Команда управления выполнения** — уведомление о выполнения текущей команды в соединении будет запущен или завершен.|
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|**Информационные** — уведомление о наличии Дополнительные сведения о текущей операции.|

|RecordsetEvent|Description|
|--------------------|-----------------|
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md), [FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|**Получение состояния** — уведомления о ходе выполнения операции извлечения данных или завершения операции получения. Эти события доступны, только если **записей** был открыт с помощью клиентского курсора.|
|[WillChangeField FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|**Управление изменить поле** — уведомление, которое приведет к изменению значение текущего поля или был изменен.|
|[WillMove, MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md), [EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|**Управления навигации** — уведомление, поместите текущую строку в **записей** изменится, был изменен или достигнут конец **записей**.|
|[WillChangeRecord RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|**Строка управления изменить** — уведомления чего-нибудь в текущей строке **записей** приведет к изменению или изменен.|
|[WillChangeRecordset RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|**Управление изменить набор записей** — уведомления чего-нибудь в текущем **записей** приведет к изменению или изменен.|

## <a name="see-also"></a>См. также:
 [Создание экземпляра события ADO языком](../../../ado/guide/data/ado-event-instantiation-by-language.md) [события ADO](../../../ado/reference/ado-api/ado-events.md) [параметры события](../../../ado/guide/data/event-parameters.md) [работе обработчики событий](../../../ado/guide/data/how-event-handlers-work-together.md) [типы событий](../../../ado/guide/data/types-of-events.md)
