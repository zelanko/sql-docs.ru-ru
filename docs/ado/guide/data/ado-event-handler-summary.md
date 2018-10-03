---
title: Общие сведения об обработчике событий ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO], about event handlers
- event handlers [ADO]
ms.assetid: b34f4472-5e04-4a2c-ab64-38d6eca31a69
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2398da9dde430d18aad38dd03cfc2816978b571c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828332"
---
# <a name="ado-connection-and-recordset-events"></a>Соединение ADO и события набора записей
Два объекта ADO может порождать события: [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта и [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта. **ConnectionEvent** семейства относится к операциям на **подключения** объекта и **RecordsetEvent** семейства относится к операциям на  **Набор записей** объекта.

-   **События подключения**: при транзакции в соединении начинается, фиксируется или откатывается назад; в то время, когда вызываются события [команда](../../../ado/reference/ado-api/command-object-ado.md) выполняется; при возникновении предупреждения во время **событие соединения**операции; или когда **подключения** начинается или заканчивается.

-   **Набор записей событий**: вызываются события по операции асинхронной выборки, а также при переходе по строкам **записей** объекта, измените поле строки **записей**, изменения строки в **записей**откройте **записей** с серверный курсор, закройте **записей**, или внести любые изменения, ни при каких обстоятельствах в  **Набор записей**.

 В следующих таблицах приведены события и их описания.

|ConnectionEvent|Описание|
|---------------------|-----------------|
|[RollbackTransComplete BeginTransComplete CommitTransComplete,](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|**Управление транзакциями** — уведомление о запуске текущей транзакции в соединении, фиксируется, или откатывается назад.|
|[WillConnect](../../../ado/reference/ado-api/willconnect-event-ado.md), [ConnectComplete, отключение](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|**Управление подключениями** — уведомление, которое запускается текущего соединения, запущен или завершен.|
|[WillExecute](../../../ado/reference/ado-api/willexecute-event-ado.md), [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)|**Команды управления выполнения** — уведомление о выполнения текущей команды в соединении будет запущен или завершен.|
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|**Информационное** — уведомление о наличии Дополнительные сведения о текущей операции.|

|RecordsetEvent|Описание|
|--------------------|-----------------|
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md), [FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|**Получение состояния** — уведомление о ходе выполнения операции по извлечению данных или завершение операции по извлечению. Эти события доступны, только если **записей** был открыт с помощью клиентского курсора.|
|[События WillChangeField, FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|**Управление изменить поле** — уведомление, которое приведет к изменению значение текущего поля или был изменен.|
|[События WillMove, MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md), [EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|**Управления навигации** — уведомление, которое позиция текущей строки в **записей** приведет к изменению, был изменен или достигнут конец **записей**.|
|[WillChangeRecord, RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|**Строка управления изменить** — уведомление чего-нибудь в текущей строке **набор записей** приведет к изменению или был изменен.|
|[События WillChangeRecordset, RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|**Управления измените набор записей** — уведомление, что нечто в текущем **записей** приведет к изменению или был изменен.|

## <a name="see-also"></a>См. также
 [Создание экземпляра события ADO языком](../../../ado/guide/data/ado-event-instantiation-by-language.md) [событий ADO](../../../ado/reference/ado-api/ado-events.md) [параметров события](../../../ado/guide/data/event-parameters.md) [совместная работа обработчиков событий](../../../ado/guide/data/how-event-handlers-work-together.md) [типы событий](../../../ado/guide/data/types-of-events.md)
