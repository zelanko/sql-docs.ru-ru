---
title: Выполнение SqlCommand с помощью SqlNotificationRequest
description: Демонстрирует настройку объекта SqlCommand для работы с уведомлением запроса.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 1ad2fd2f29c7218d1da0535ca089e2648d4b0cf0
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80918688"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Выполнение SqlCommand с помощью SqlNotificationRequest

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

<xref:Microsoft.Data.SqlClient.SqlCommand> можно настроить на генерацию уведомления об изменении данных после их получения с сервера, и в случае повторного выполнения запроса результирующий набор будет отличаться. Это полезно для сценариев, в которых необходимо использовать пользовательские очереди уведомлений на сервере, или если не требуется поддерживать активные объекты.

## <a name="creating-the-notification-request"></a>Создание запроса на уведомление

Объект <xref:Microsoft.Data.Sql.SqlNotificationRequest> можно использовать для создания запроса на уведомление путем привязки его к объекту `SqlCommand`. Объект `SqlNotificationRequest` больше не понадобится после создания запроса. Вы можете запросить очередь для любых уведомлений и ответить соответствующим образом. Уведомления могут возникать, даже если приложение завершает работу и впоследствии перезапускается.

Если выполняется команда со связанным уведомлением, любые изменения в исходном результирующем наборе инициируют отправку сообщения в очередь SQL Server, которая была указана в запросе уведомления.

Опрос очереди SQL Server и интерпретация сообщения зависят от конкретного приложения. Приложение отвечает за опрос очереди и реагирование на основе содержимого сообщения.

> [!NOTE]
> При использовании запросов SQL Server на уведомления с помощью <xref:Microsoft.Data.SqlClient.SqlDependency>создайте свое собственное имя очереди вместо использования имени службы по умолчанию.

Для<xref:Microsoft.Data.Sql.SqlNotificationRequest> не существует новых элементов безопасности на стороне клиента. Это, в первую очередь, функция сервера, и сервер создал специальные разрешения, которые необходимы пользователям, чтобы запрашивать уведомления.

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
