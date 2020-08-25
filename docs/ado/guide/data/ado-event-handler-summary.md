---
description: События подключения ADO и записи в набор записей
title: Сводка по обработчику событий ADO | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 46e352b88ea24d264ccde8a4d3932f748082723b
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806457"
---
# <a name="ado-connection-and-recordset-events"></a>События подключения ADO и записи в набор записей
События могут создаваться двумя объектами ADO: объектом [соединения](../../reference/ado-api/connection-object-ado.md) и объектом [Recordset](../../reference/ado-api/recordset-object-ado.md) . Семейство **коннектионевент** относится к операциям объекта **Connection** , а семейство **рекордсетевент** относится к операциям с объектом **Recordset** .

-   **События соединения**: события выдаются, когда начинается транзакция в соединении, фиксируется или выполняется откат. При выполнении [команды](../../reference/ado-api/command-object-ado.md) ; При возникновении предупреждения в ходе операции **события соединения** ; или при запуске или завершении **соединения** .

-   **События набора записей**. события выдаются вокруг асинхронных операций выборки, а также при переходе по строкам объекта **Recordset** , изменению поля в строке **набора записей**, изменению строки в **наборе записей**, открытию **набора** записей с серверным курсором, закрытию **набора записей**или внесению любых изменений в **набор записей**.

 В следующих таблицах приводится сводка по событиям и их описаниям.

|коннектионевент|Описание|
|---------------------|-----------------|
|[Бегинтранскомплете, Коммиттранскомплете, Роллбакктранскомплете](../../reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|**Управление транзакциями** — уведомление о том, что текущая транзакция соединения была запущена, зафиксирована или произведена откат.|
|[Виллконнект](../../reference/ado-api/willconnect-event-ado.md), [коннекткомплете, отключение](../../reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|**Управление подключением** — уведомление о том, что текущее подключение будет запущено, начато или завершено.|
|[WillExecute](../../reference/ado-api/willexecute-event-ado.md), [ексекутекомплете](../../reference/ado-api/executecomplete-event-ado.md)|**Управление выполнением команд** — уведомление о том, что выполнение текущей команды в соединении будет начато или завершено.|
|[InfoMessage](../../reference/ado-api/infomessage-event-ado.md)|**Информационное** уведомление о наличии дополнительных сведений о текущей операции.|

|рекордсетевент|Описание|
|--------------------|-----------------|
|[Фетчпрогресс](../../reference/ado-api/fetchprogress-event-ado.md), [фетчкомплете](../../reference/ado-api/fetchcomplete-event-ado.md)|**Состояние извлечения** — уведомление о ходе выполнения операции получения данных или о завершении операции извлечения. Эти события доступны только в том случае, если **набор записей** был открыт с помощью курсора на стороне клиента.|
|[Виллчанжефиелд, Фиелдчанжекомплете](../../reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|**Управление изменениями полей** — уведомление о том, что значение текущего поля изменится или изменилось.|
|[Виллмове, мовекомплете](../../reference/ado-api/willmove-and-movecomplete-events-ado.md), [ендофрекордсет](../../reference/ado-api/endofrecordset-event-ado.md)|**Управление навигацией** — уведомление о том, что текущее расположение строки в **наборе записей** изменится, изменилось или достигло конца **набора записей**.|
|[WillChangeRecord, RecordChangeComplete](../../reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|**Управление изменениями строк** — уведомление о том, что что-то в текущей строке **набора записей** изменится или изменилось.|
|[Виллчанжерекордсет, Рекордсетчанжекомплете](../../reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|**Управление изменениями в наборе записей** — уведомление о том, что что-либо в текущем **наборе записей** изменится или изменилось.|

## <a name="see-also"></a>См. также
 [Параметры событий](./event-parameters.md) ADO " [Создание экземпляра события](./ado-event-instantiation-by-language.md) [ADO](../../reference/ado-api/ado-events.md) ". [как обработчики событий работают вместе](./how-event-handlers-work-together.md) с [типами событий](./types-of-events.md)