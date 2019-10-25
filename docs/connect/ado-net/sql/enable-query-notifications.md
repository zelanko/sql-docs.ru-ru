---
title: Включение уведомлений запросов
description: Описывает использование уведомлений о запросах, включая требования для их включения и использования.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 94b472a1fe040aa3a684d9f7b523ba09c82a651e
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452232"
---
# <a name="enabling-query-notifications"></a>Включение уведомлений запросов

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Приложения, использующие уведомления о запросах, имеют общий набор требований. Чтобы поддерживать уведомления о запросах, источник данных SQL должен быть правильно настроен, а пользователь должен иметь соответствующие права доступа на стороне клиента и сервера.  
  
Чтобы использовать уведомления о запросах, необходимо выполнить следующие действия.  
  
- Включение уведомлений о запросах для базы данных.  
  
- Убедитесь, что идентификатор пользователя, используемый для подключения к базе данных, имеет необходимые разрешения.  
  
- Используйте объект <xref:Microsoft.Data.SqlClient.SqlCommand> для выполнения допустимой инструкции SELECT со связанным объектом уведомления — либо <xref:Microsoft.Data.SqlClient.SqlDependency>, либо <xref:Microsoft.Data.Sql.SqlNotificationRequest>.  
  
- Укажите код для обработки уведомления, если отслеживаемые данные изменяются.  
  
## <a name="query-notifications-requirements"></a>Требования к уведомлениям о запросах  
Уведомления о запросах поддерживаются только для инструкций SELECT, соответствующих списку конкретных требований. В следующей таблице приведены ссылки на документацию по Service Broker и уведомлениям о запросах в электронная документация на SQL Server.  
  
**Документация по SQL Server**  
  
- [Создание запроса для уведомления](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Вопросы безопасности, связанные с компонентом Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))  
  
- [Защита и обеспечение безопасности (компонент Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))  
  
- [Вопросы безопасности, связанные со службами уведомления](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))  
  
- [Права доступа для уведомлений о запросах](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))  
  
- [Вопросы интернационализации, связанные с компонентом Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))  
  
- [Вопросы проектирования решений (компонент Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))  
  
- [Информационный центр по компоненту Service Broker для разработчиков](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Руководство разработчика (компонент Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Включение уведомлений о запросах для запуска примера кода  
Чтобы включить компонент Service Broker для базы данных **AdventureWorks** с помощью среды SQL Server Management Studio, выполните следующую инструкцию Transact-SQL.  
  
`ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
Чтобы образцы уведомлений о запросах выполнялись правильно, на сервере базы данных должны быть выполнены следующие инструкции Transact-SQL.  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Разрешения уведомлений о запросах  
Пользователи, выполняющие команды, запрашивающие уведомление, должны иметь разрешение на отправку запросов уведомления базы данных на сервере.  
  
Для кода на стороне клиента, который выполняется в ситуации частичного доверия, требуется <xref:Microsoft.Data.SqlClient.SqlClientPermission>.  
  
Следующий код создает объект <xref:Microsoft.Data.SqlClient.SqlClientPermission>, устанавливая <xref:System.Security.Permissions.PermissionState> в значение <xref:System.Security.Permissions.PermissionState.Unrestricted>. <xref:System.Security.CodeAccessPermission.Demand%2A> будет принудительно выполнять <xref:System.Security.SecurityException> во время выполнения, если всем вызывающим объектам выше в стеке вызовов не было предоставлено разрешение.  
  
[!code-csharp[DataWorks SqlClientPermission_Demand#1](~/../sqlclient/doc/samples/SqlClientPermission_Demand.cs#1)]
  
## <a name="choosing-a-notification-object"></a>Выбор объекта уведомления  
API-интерфейс уведомлений о запросах предоставляет два объекта для обработки уведомлений: <xref:Microsoft.Data.SqlClient.SqlDependency> и <xref:Microsoft.Data.Sql.SqlNotificationRequest>.
  
### <a name="using-sqldependency"></a>Использование SqlDependency  
Чтобы вы могли использовать объект <xref:Microsoft.Data.SqlClient.SqlDependency>, в используемой базе данных SQL Server должен быть включен компонент Service Broker, а пользователи должны иметь права для получения уведомлений. Service Broker объекты, такие как очередь уведомлений, являются предопределенными.  
  
Кроме того, <xref:Microsoft.Data.SqlClient.SqlDependency> автоматически запускает рабочий поток для обработки уведомлений по мере их отправки в очередь. Он также анализирует Service Broker сообщение, предоставляя сведения в виде данных аргумента события. <xref:Microsoft.Data.SqlClient.SqlDependency> должны быть инициализированы путем вызова метода `Start`, чтобы установить зависимость от базы данных. Это статический метод, который должен вызываться только один раз при инициализации приложения для каждого необходимого подключения к базе данных. Метод `Stop` должен вызываться при завершении приложения для каждого установленного соединения зависимости.  
  
### <a name="using-sqlnotificationrequest"></a>Использование SqlNotificationRequest  
Напротив, <xref:Microsoft.Data.Sql.SqlNotificationRequest> требует самостоятельно реализовать всю инфраструктуру прослушивания. Кроме того, должны быть определены все вспомогательные Service Broker объекты, такие как очередь, служба и типы сообщений, поддерживаемые очередью. Этот подход вручную удобен, если приложению требуются специальные уведомления или поведения уведомлений, или если приложение входит в состав более крупного Service Broker приложения.  
  
## <a name="next-steps"></a>Следующие шаги
- [Уведомления запросов в SQL Server](query-notifications-sql-server.md)
