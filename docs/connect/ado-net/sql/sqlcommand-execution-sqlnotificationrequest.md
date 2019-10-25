---
title: Выполнение SqlCommand с помощью SqlNotificationRequest
description: Демонстрирует настройку объекта SqlCommand для работы с уведомлением о запросе.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 892f11e2d81e3a0733a1f0747c0b72c72ebc79fc
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451946"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Выполнение SqlCommand с помощью SqlNotificationRequest

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

<xref:Microsoft.Data.SqlClient.SqlCommand> можно настроить для создания уведомления об изменении данных после его получения с сервера, и результирующий набор будет отличаться, если запрос был выполнен снова. Это полезно для сценариев, в которых необходимо использовать пользовательские очереди уведомлений на сервере или если не требуется поддерживать активные объекты.

## <a name="creating-the-notification-request"></a>Создание запроса на уведомление

Можно использовать объект <xref:Microsoft.Data.Sql.SqlNotificationRequest> для создания запроса уведомления путем привязки его к `SqlCommand` объекту. После создания запроса больше не требуется объект `SqlNotificationRequest`. Можно запросить очередь на получение уведомлений и соответствующим образом реагировать на них. Уведомления могут возникать даже в том случае, если приложение завершает работу и впоследствии перезапускается.

Если выполняется команда со связанным уведомлением, любые изменения в исходном результирующем наборе инициируют отправку сообщения в очередь SQL Server, которая была указана в запросе уведомления.

Опрос очереди SQL Server и интерпретация сообщения зависят от конкретного приложения. Приложение отвечает за опрос очереди и на основе содержимого сообщения.

> [!NOTE]
> При использовании SQL Server запросов уведомлений с <xref:Microsoft.Data.SqlClient.SqlDependency> создайте собственное имя очереди вместо использования имени службы по умолчанию.

Для <xref:Microsoft.Data.Sql.SqlNotificationRequest> не существует новых элементов безопасности на стороне клиента. В основном это компонент сервера, и сервер создал специальные привилегии, которые необходимы пользователям для запроса уведомления.

### <a name="example"></a>Пример

В следующем фрагменте кода показано, как создать <xref:Microsoft.Data.Sql.SqlNotificationRequest> и связать его с <xref:Microsoft.Data.SqlClient.SqlCommand>.

```csharp
// Assume connection is an open SqlConnection.
// Create a new SqlCommand object.
SqlCommand command=new SqlCommand(
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);

// Create a SqlNotificationRequest object.
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="next-steps"></a>Дальнейшие действия
- [Уведомления запросов в SQL Server](query-notifications-sql-server.md)
