---
title: Уведомления запросов в SQL Server
description: Сведения о том, как приложения .NET могут запрашивать от SQL Server уведомления об изменении данных.
ms.date: 08/15/2019
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: d3905604b45eec2f1e9c7c1c93bd53b1863695f3
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925470"
---
# <a name="query-notifications-in-sql-server"></a>Уведомления запросов в SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

С помощью уведомлений о запросах, построенных на основе инфраструктуры компонента Service Broker, приложения могут получать извещения об изменениях данных. Эта функция особенно полезна для приложений, которые предоставляют кэш данных из базы данных (например, для веб-приложений), и которым требуются уведомления об изменении исходных данных.  
  
Существует три способа реализации уведомлений о запросах с помощью ADO.NET:  
  
- Реализация низкого уровня обеспечивается классом `SqlNotificationRequest`, который предоставляет функциональные возможности на стороне сервера, что позволяет выполнять команду с запросом на уведомления.  
  
- Высокоуровневая реализация обеспечивается классом `SqlDependency`, который является классом, предоставляющим высокоуровневую абстракцию функций уведомления между исходным приложением и SQL Server, что позволяет использовать зависимость для обнаружения изменений на сервере. В большинстве случаев это самый простой и самый эффективный способ задействовать возможности уведомления SQL Server в управляемых клиентских приложениях с помощью поставщика данных Microsoft SqlClient для SQL Server.  
  
- Кроме того, веб-приложения, построенные с помощью ASP.NET 2.0 и более поздних версий, могут использовать вспомогательные классы `SqlCacheDependency`.  
  
Уведомления о запросах удобно использовать в приложениях, которые должны обновлять дисплеи и кэши в ответ на изменения в базовых данных. Microsoft SQL Server позволяет приложениям .NET передавать команды в SQL Server и запрашивать уведомления, если выполнение одной и той же команды принесет результирующий набор, отличный от полученного первоначально. Формируемые на сервере уведомления отправляются через очереди для последующей обработки.  
  
Уведомления можно настроить для инструкций SELECT и EXECUTE. При использовании инструкции EXECUTE SQL Server регистрирует уведомление о выполненной команде, а не саму инструкцию EXECUTE. Команда должна соответствовать требованиям, предъявляемым к инструкции SELECT. Если регистрируемая команда состоит из нескольких инструкций, ядро СУБД создает уведомления для каждой из них.  
  
При разработке приложения, где нужны надежные, передаваемые за доли секунды уведомления об изменении данных, см. подразделы **Планирование эффективной стратегии уведомлений о запросах** и **Альтернативные подходы к уведомлениям о запросах** в разделе [Планирование уведомлений](https://go.microsoft.com/fwlink/?LinkId=211984) электронной документации на SQL Server. Дополнительные сведения об уведомлениях о запросах и SQL Server Service Broker см. по следующим ссылкам в электронной документации на SQL Server.  
  
**Документация по SQL Server**  
  
- [Использование уведомлений запросов](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))  
  
- [Создание запроса для уведомления](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Разработка (компонент Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))  
  
- [Информационный центр по компоненту Service Broker для разработчиков](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Руководство разработчика (компонент Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="in-this-section"></a>В этом разделе  
[Включение уведомлений запросов](enable-query-notifications.md)  
Описание использования уведомлений о запросах, включая требования для их включения и использования.  
  
[SqlDependency в приложении ASP.NET](sqldependency-aspnet-app.md)  
Демонстрирует использование уведомлений запросов из приложения ASP.NET.  
  
[Обнаружение изменений с использованием SqlDependency](detect-changes-sqldependency.md)  
Сведения об определении отличия результатов запроса от изначально полученных.  
  
[Выполнение SqlCommand с помощью SqlNotificationRequest](sqlcommand-execution-sqlnotificationrequest.md)  
Демонстрирует настройку объекта <xref:Microsoft.Data.SqlClient.SqlCommand> для работы с уведомлением запроса.  
  
## <a name="reference"></a>Справочник  
<xref:Microsoft.Data.Sql.SqlNotificationRequest>  
Описание класса <xref:Microsoft.Data.Sql.SqlNotificationRequest> и всех его членов.  
  
<xref:Microsoft.Data.SqlClient.SqlDependency>  
Описание класса <xref:Microsoft.Data.SqlClient.SqlDependency> и всех его членов.  
  
<xref:System.Web.Caching.SqlCacheDependency>  
Описание класса <xref:System.Web.Caching.SqlCacheDependency> и всех его членов.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [SQL Server и ADO.NET](index.md)
