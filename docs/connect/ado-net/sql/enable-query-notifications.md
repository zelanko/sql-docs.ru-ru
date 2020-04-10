---
title: Включение уведомлений запросов
description: Описание использования уведомлений о запросах, включая требования для их включения и использования.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 2648f8efbae6cc6665ea3ab984b27012a2a1ebc7
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920430"
---
# <a name="enabling-query-notifications"></a>Включение уведомлений запросов

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Приложения, использующие уведомления о запросах, имеют общий набор требований. Чтобы поддерживать уведомления о запросах, источник данных SQL должен быть правильно настроен, а пользователь должен иметь соответствующие права доступа на стороне клиента и сервера.  
  
Чтобы использовать уведомления о запросах, сделайте следующее:  
  
- Включите уведомления о запросах для своей базы данных.  
  
- Предоставьте идентификатору пользователя, используемому для подключения к базе данных, необходимые разрешения.  
  
- Используйте объект <xref:Microsoft.Data.SqlClient.SqlCommand> для выполнения допустимой инструкции SELECT со связанным объектом уведомления: <xref:Microsoft.Data.SqlClient.SqlDependency> или <xref:Microsoft.Data.Sql.SqlNotificationRequest>.  
  
- Укажите код для обработки уведомления в случае изменения отслеживаемых данных.  
  
## <a name="query-notifications-requirements"></a>Требования к уведомлениям о запросах  
Уведомления о запросах поддерживаются только для инструкций SELECT, которые соответствуют конкретным требованиям. В приведенной ниже таблице указаны ссылки на статьи о компоненте Service Broker и уведомлениях о запросах в электронной документации по SQL Server.  
  
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
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Настройка уведомлений о запросах для выполнения примера кода  
Чтобы включить компонент Service Broker для базы данных **AdventureWorks** с помощью среды SQL Server Management Studio, выполните следующую инструкцию Transact-SQL.  
  
`ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
Для правильного запуска примеров уведомлений о запросах необходимо выполнить на сервере базы данных приведенные ниже инструкции Transact-SQL.  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Разрешения на уведомления о запросах  
Пользователям, выполняющим команды для запроса уведомлений, необходимо разрешение базы данных SUBSCRIBE QUERY NOTIFICATIONS на сервере.  
  
Код на стороне клиента, который выполняется в случае частичного доверия, требует разрешения <xref:Microsoft.Data.SqlClient.SqlClientPermission>.  
  
Следующий код создает объект <xref:Microsoft.Data.SqlClient.SqlClientPermission>, устанавливая для <xref:System.Security.Permissions.PermissionState> значение <xref:System.Security.Permissions.PermissionState.Unrestricted>. <xref:System.Security.CodeAccessPermission.Demand%2A> принудительно создает <xref:System.Security.SecurityException> во время выполнения, если все вызывающие методы, расположенные выше в стеке вызовов, не получили разрешения.  
  
[!code-csharp[DataWorks SqlClientPermission_Demand#1](~/../sqlclient/doc/samples/SqlClientPermission_Demand.cs#1)]
  
## <a name="choosing-a-notification-object"></a>Выбор объекта уведомления  
API-интерфейс уведомлений о запросах предоставляет два объекта для обработки уведомлений: <xref:Microsoft.Data.SqlClient.SqlDependency> и <xref:Microsoft.Data.Sql.SqlNotificationRequest>.
  
### <a name="using-sqldependency"></a>Использование SqlDependency  
Чтобы вы могли использовать объект <xref:Microsoft.Data.SqlClient.SqlDependency>, в используемой базе данных SQL Server должен быть включен компонент Service Broker, а пользователи должны иметь права для получения уведомлений. Объекты компонента Service Broker, такие как очередь уведомлений, предопределены.  
  
Кроме того, объект <xref:Microsoft.Data.SqlClient.SqlDependency> автоматически запускает рабочий поток для обработки уведомлений по мере их поступления в очередь. Он также проводит синтаксический анализ сообщения компонента Service Broker, предоставляя данные в виде аргументов событий. Экземпляр <xref:Microsoft.Data.SqlClient.SqlDependency> создается путем вызова метода `Start`, который устанавливает зависимость с базой данных. Это статический метод, который необходимо вызывать только один раз во время инициализации приложения для каждого требуемого подключения к базе данных. Метод `Stop` необходимо вызывать при завершении приложения для каждого установленного подключения зависимости.  
  
### <a name="using-sqlnotificationrequest"></a>Использование SqlNotificationRequest  
В то же время <xref:Microsoft.Data.Sql.SqlNotificationRequest> требует реализации всей инфраструктуры прослушивания вручную. Кроме того, необходимо будет определить все поддерживающие объекты компонента Service Broker, такие как очередь, служба и типы сообщений, поддерживаемые очередью. Этот ручной подход полезен, если для вашего приложения требуются специальные сообщения с уведомлениями или параметры уведомлений или же если ваше приложение является частью более крупного приложения Service Broker.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Уведомления запросов в SQL Server](query-notifications-sql-server.md)
