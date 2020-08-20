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
ms.openlocfilehash: 92d1dcd202c4e115cda4198f90e3410c2cb44319
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453846"
---
# <a name="ado-connection-and-recordset-events"></a>События подключения ADO и записи в набор записей
События могут создаваться двумя объектами ADO: объектом [соединения](../../../ado/reference/ado-api/connection-object-ado.md) и объектом [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) . Семейство **коннектионевент** относится к операциям объекта **Connection** , а семейство **рекордсетевент** относится к операциям с объектом **Recordset** .

-   **События соединения**: события выдаются, когда начинается транзакция в соединении, фиксируется или выполняется откат. При выполнении [команды](../../../ado/reference/ado-api/command-object-ado.md) ; При возникновении предупреждения в ходе операции **события соединения** ; или при запуске или завершении **соединения** .

-   **События набора записей**. события выдаются вокруг асинхронных операций выборки, а также при переходе по строкам объекта **Recordset** , изменению поля в строке **набора записей**, изменению строки в **наборе записей**, открытию **набора** записей с серверным курсором, закрытию **набора записей**или внесению любых изменений в **набор записей**.

 В следующих таблицах приводится сводка по событиям и их описаниям.

|коннектионевент|Описание|
|---------------------|-----------------|
|[Бегинтранскомплете, Коммиттранскомплете, Роллбакктранскомплете](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|**Управление транзакциями** — уведомление о том, что текущая транзакция соединения была запущена, зафиксирована или произведена откат.|
|[Виллконнект](../../../ado/reference/ado-api/willconnect-event-ado.md), [коннекткомплете, отключение](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|**Управление подключением** — уведомление о том, что текущее подключение будет запущено, начато или завершено.|
|[WillExecute](../../../ado/reference/ado-api/willexecute-event-ado.md), [ексекутекомплете](../../../ado/reference/ado-api/executecomplete-event-ado.md)|**Управление выполнением команд** — уведомление о том, что выполнение текущей команды в соединении будет начато или завершено.|
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|**Информационное** уведомление о наличии дополнительных сведений о текущей операции.|

|рекордсетевент|Описание|
|--------------------|-----------------|
|[Фетчпрогресс](../../../ado/reference/ado-api/fetchprogress-event-ado.md), [фетчкомплете](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|**Состояние извлечения** — уведомление о ходе выполнения операции получения данных или о завершении операции извлечения. Эти события доступны только в том случае, если **набор записей** был открыт с помощью курсора на стороне клиента.|
|[Виллчанжефиелд, Фиелдчанжекомплете](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|**Управление изменениями полей** — уведомление о том, что значение текущего поля изменится или изменилось.|
|[Виллмове, мовекомплете](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md), [ендофрекордсет](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|**Управление навигацией** — уведомление о том, что текущее расположение строки в **наборе записей** изменится, изменилось или достигло конца **набора записей**.|
|[WillChangeRecord, RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|**Управление изменениями строк** — уведомление о том, что что-то в текущей строке **набора записей** изменится или изменилось.|
|[Виллчанжерекордсет, Рекордсетчанжекомплете](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|**Управление изменениями в наборе записей** — уведомление о том, что что-либо в текущем **наборе записей** изменится или изменилось.|

## <a name="see-also"></a>См. также
 [Параметры событий](../../../ado/guide/data/event-parameters.md) ADO " [Создание экземпляра события](../../../ado/guide/data/ado-event-instantiation-by-language.md) [ADO](../../../ado/reference/ado-api/ado-events.md) ". [как обработчики событий работают вместе](../../../ado/guide/data/how-event-handlers-work-together.md) с [типами событий](../../../ado/guide/data/types-of-events.md)
