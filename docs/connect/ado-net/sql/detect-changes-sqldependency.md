---
title: Обнаружение изменений с использованием SqlDependency
description: Сведения об определении отличия результатов запроса от изначально полученных.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 6a003670c15ac95b6f0a5f70d0997c1c854b089e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75247823"
---
# <a name="detecting-changes-with-sqldependency"></a>Обнаружение изменений с использованием SqlDependency

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Объект <xref:Microsoft.Data.SqlClient.SqlDependency> может быть связан с <xref:Microsoft.Data.SqlClient.SqlCommand> для определения отличия результатов запроса от изначально полученных. Вы также можете назначить делегата событию `OnChange`, которое сработает при изменении результатов для связанной команды. Объект <xref:Microsoft.Data.SqlClient.SqlDependency> необходимо связать с командой перед ее выполнением. Свойство `HasChanges` объекта <xref:Microsoft.Data.SqlClient.SqlDependency> также можно использовать для определения изменений результатов запроса с момента первого извлечения данных.

## <a name="security-considerations"></a>Вопросы безопасности

Инфраструктура зависимостей зависит от объекта <xref:Microsoft.Data.SqlClient.SqlConnection>, открытого при вызове <xref:Microsoft.Data.SqlClient.SqlDependency.Start%2A>, для получения уведомлений об изменении базовых данных для данной команды. Возможность для клиента инициировать вызов `SqlDependency.Start` контролируется с помощью <xref:Microsoft.Data.SqlClient.SqlClientPermission> и атрибутов управления доступом для кода. Дополнительные сведения см. в статье [Включение уведомлений запросов](enable-query-notifications.md).

### <a name="example"></a>Пример

Ниже приведены шаги для объявления зависимости, выполнения команды и получения уведомления при изменении результирующего набора:

1. Создает соединение `SqlDependency` с сервером.

2. Создайте объекты <xref:Microsoft.Data.SqlClient.SqlConnection> и <xref:Microsoft.Data.SqlClient.SqlCommand> для подключения к серверу и определения инструкции Transact-SQL.

3. Создайте новый объект `SqlDependency` или используйте имеющийся, привязав его к объекту `SqlCommand`. На внутреннем уровне будет создан объект <xref:Microsoft.Data.Sql.SqlNotificationRequest>, который при необходимости может быть привязан к объекту команды. Данный запрос на уведомление содержит внутренний идентификатор, который однозначно идентифицирует этот объект `SqlDependency`. Он также запускает прослушиватель клиента, если он еще не активен.

4. Добавьте для обработчика события подписку на событие `OnChange` объекта `SqlDependency`.

5. Выполните команду, используя любой из методов `Execute` объекта `SqlCommand`. Так как команда связана с объектом уведомления, сервер распознает, что он должен сгенерировать уведомление, и информация об очереди будет указывать на очередь зависимостей.

6. Остановите подключение объекта `SqlDependency` к серверу.

Если впоследствии какой-либо пользователь изменит базовые данные, Microsoft SQL Server обнаружит уведомление, ожидающее такое изменение, и опубликует уведомление, которое обрабатывается и пересылается клиенту через базовый объект `SqlConnection`, созданный путем вызова `SqlDependency.Start`. Прослушиватель клиента получит сообщение о недействительности. Затем прослушиватель клиента найдет связанный объект `SqlDependency` и запустит событие `OnChange`.

В приведенном ниже фрагменте кода показан конструктивный шаблон, который необходимо использовать для создания примера приложения.

```csharp
void Initialization()
{
    // Create a dependency connection.
    SqlDependency.Start(connectionString, queueName);
}

void SomeMethod()
{
    // Assume connection is an open SqlConnection.

    // Create a new SqlCommand object.
    using (SqlCommand command=new SqlCommand(
        "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers",
        connection))
    {

        // Create a dependency and associate it with the SqlCommand.
        SqlDependency dependency=new SqlDependency(command);
        // Maintain the reference in a class member.

        // Subscribe to the SqlDependency event.
        dependency.OnChange+=new
           OnChangeEventHandler(OnDependencyChange);

        // Execute the command.
        using (SqlDataReader reader = command.ExecuteReader())
        {
            // Process the DataReader.
        }
    }
}

// Handler method
void OnDependencyChange(object sender,
   SqlNotificationEventArgs e )
{
  // Handle the event (for example, invalidate this cache entry).
}

void Termination()
{
    // Release the dependency.
    SqlDependency.Stop(connectionString, queueName);
}
```

## <a name="next-steps"></a>Дальнейшие действия
- [Уведомления запросов в SQL Server](query-notifications-sql-server.md)
