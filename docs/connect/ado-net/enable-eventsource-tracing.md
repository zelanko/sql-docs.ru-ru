---
title: Включение трассировки событий в SqlClient
description: Описывает включение трассировки событий в SqlClient путем реализации прослушивателя событий и доступа к данным события.
ms.date: 06/15/2020
dev_langs:
- csharp
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: johnnypham
ms.author: v-jopha
ms.reviewer: ''
ms.openlocfilehash: 17e947c108d14accb880dbd6673231e82b0b133c
ms.sourcegitcommit: 6b3569977b034554883a94d73d1c4df6e2f74fe2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2020
ms.locfileid: "85110167"
---
# <a name="enabling-event-tracing-in-sqlclient"></a>Включение трассировки событий в SqlClient

[!INCLUDE [appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE [Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

[Средство трассировки событий для Windows (ETW)](https://docs.microsoft.com/windows/win32/etw/event-tracing-portal) является эффективным средством трассировки на уровне ядра, которое позволяет записывать в журнал события, определяемые драйвером, в целях отладки и тестирования. SqlClient поддерживает запись событий ETW на разных информационных уровнях. Чтобы начать сбор трассировок событий, клиентские приложения должны прослушивать события от реализации EventSource для SqlClient.

```
Microsoft.Data.SqlClient.EventSource
```

Текущая реализация поддерживает следующие ключевые слова событий.

| Имя ключевого слова | Значение | Описание: |
| ------------ | ----- | ----------- |
| ExecutionTrace | 1 | Включает запись событий запуска и приостанавливается до и после выполнения команды. |
| Трассировка | 2 | Включает запись основных событий трассировки потока приложений. |
| Область | 4 | Включает запись событий входа и выхода. |
| NotificationTrace | 8 | Включает запись событий трассировки `SqlNotification`. |
| NotificationScope | 16 | Включает запись событий входа в область `SqlNotification` и выхода из нее. |
| PoolerTrace | 32 | Включает запись событий трассировки потока для пула соединений. |
| PoolerScope | 64 | Включает запись событий трассировки области пула соединений. |
| AdvancedTrace | 128 | Включает запись событий расширенной трассировки потока. |
| AdvancedTraceBin  | 256 | Включает запись событий расширенной трассировки потока с дополнительными сведениями. |
| CorrelationTrace | 512 | Включает запись событий трассировки потока корреляции. |
| StateDump | 1024 | Включает запись дампа полного состояния `SqlConnection`. |
| SNITrace | 2048 | Включает запись событий трассировки потока из реализации управляемой сети (применимо только в .NET Core). |
| SNIScope | 4096 | Включает запись событий области из реализации управляемой сети (применимо только в .NET Core). |
|||

## <a name="example"></a>Пример
В следующем примере включается трассировка событий для операции с данными в образце базы данных **AdventureWorks** и отображаются события в окне консоли.

[!code-csharp [SqlClientEventSource#1](~/../sqlclient/doc/samples/SqlClientEventSource.cs#1)]

## <a name="external-resources"></a>Внешние ресурсы  
Для получения дополнительных сведений см. следующие ресурсы.  
  
|Ресурс|Описание|  
|--------------|-----------------|  
|[EventSource](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource)|Предоставляет возможность создания событий ETW.| 
|[Класс EventListener](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventlistener)|Предоставляет методы для включения и отключения событий из источников событий.| 
