---
title: Обнаружение изменений с использованием SqlDependency
description: Показывает, как определить, когда результаты запроса будут отличаться от полученных изначально.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 2d2c4c48a9085fa83d6104233be5f2e1c6b11318
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452244"
---
# <a name="detecting-changes-with-sqldependency"></a>Обнаружение изменений с использованием SqlDependency

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Объект <xref:Microsoft.Data.SqlClient.SqlDependency> может быть связан с <xref:Microsoft.Data.SqlClient.SqlCommand>, чтобы обнаружить, когда результаты запроса отличаются от первоначально извлеченных. Можно также назначить делегату событию `OnChange`, которое будет срабатывать при изменении результатов для связанной команды. Перед выполнением команды необходимо связать <xref:Microsoft.Data.SqlClient.SqlDependency> с командой. Свойство `HasChanges` <xref:Microsoft.Data.SqlClient.SqlDependency> также можно использовать, чтобы определить, изменились ли результаты запроса с момента первого извлечения данных.

## <a name="security-considerations"></a>Вопросы безопасности

Инфраструктура зависимостей зависит от <xref:Microsoft.Data.SqlClient.SqlConnection>, которая открывается при вызове <xref:Microsoft.Data.SqlClient.SqlDependency.Start%2A>, чтобы получать уведомления о том, что базовые данные были изменены для данной команды. Возможность клиента инициировать вызов `SqlDependency.Start` контролируется с помощью <xref:Microsoft.Data.SqlClient.SqlClientPermission> и атрибутов управления доступом для кода. Дополнительные сведения см. в разделе [Включение уведомлений о запросах](enable-query-notifications.md).

### <a name="example"></a>Пример

Следующие шаги иллюстрируют, как объявить зависимость, выполнить команду и получить уведомление при изменении результирующего набора:

1. Создает соединение `SqlDependency` с сервером.

2. Создание <xref:Microsoft.Data.SqlClient.SqlConnection> и <xref:Microsoft.Data.SqlClient.SqlCommand> объектов для подключения к серверу и определения инструкции Transact-SQL.

3. Создайте новый объект `SqlDependency` или используйте существующий, а затем привяжите его к объекту `SqlCommand`. На внутреннем уровне он создает объект <xref:Microsoft.Data.Sql.SqlNotificationRequest> и привязывает его к объекту Command по мере необходимости. Этот запрос уведомления содержит внутренний идентификатор, который однозначно определяет этот `SqlDependency` объект. Он также запускает прослушиватель клиента, если он еще не активен.

4. Подпишите обработчик событий на `OnChange` событие объекта `SqlDependency`.

5. Выполните команду, используя любой из `Execute`ных методов объекта `SqlCommand`. Поскольку команда привязана к объекту уведомления, сервер распознает, что он должен создать уведомление, и сведения об очереди будут указывать на очередь зависимостей.

6. Останавливает `SqlDependency` подключение к серверу.

Если какой-либо пользователь изменяет базовые данные, Microsoft SQL Server обнаруживает, что для такого изменения ожидается уведомление, и отправляет уведомление, которое обрабатывается и перенаправляется клиенту через базовую `SqlConnection`, созданную вызов `SqlDependency.Start`. Прослушиватель клиента получает сообщение о недействительности. Затем прослушиватель клиента находит связанный объект `SqlDependency` и запускает событие `OnChange`.

В следующем фрагменте кода показан шаблон проектирования, который будет использоваться для создания примера приложения.

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
