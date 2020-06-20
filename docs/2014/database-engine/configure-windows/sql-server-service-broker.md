---
title: SQL Server Service Broker | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.SSBQUEUEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBREMSVCBINDPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBMSGTYPEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBROUTEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBCONTRACTPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBSERVICEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBPRIORITYPROPERTIES.GENERAL.F1
helpviewer_keywords:
- Broker See Service Broker
- SQL Server Service Broker
- Service Broker
ms.assetid: 8b8b3b57-fd46-44de-9a4e-e3a8e3999c1e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3d3877dd8311e0fe5b65bd4b1e7f9c40fbd84751
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934815"
---
# <a name="sql-server-service-broker"></a>Служба SQL Server Service Broker
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssSB](../../includes/sssb-md.md)]обеспечивает встроенную поддержку приложений обмена сообщениями и очередей в [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . Это облегчает разработчикам создание сложных приложений, использующих компоненты [!INCLUDE[ssDE](../../includes/ssde-md.md)] для связи между разнородными базами данных. Разработчики могут использовать компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] для облегчения создания распределенных и надежных приложений.  
  
 Разработчики приложений, использующие компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] , могут распределять рабочую нагрузку между несколькими базами данных без программирования сложного взаимодействия и создания внутреннего обмена сообщениями. Это сокращает разработку и проверочную работу, потому что компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] обеспечивает взаимодействие в контексте диалога. Кроме того, это повышает производительность. Например, сервер, обслуживающий клиентские запросы базы данных, поддерживающие веб-сайты, может записывать информацию и отправлять ресурсоемкие задачи в очереди серверных баз данных. [!INCLUDE[ssSB](../../includes/sssb-md.md)] гарантирует, что управление всеми задачами ведется в контексте транзакций, чтобы обеспечить надежность и техническое единообразие.  
  
## <a name="where-is-the-documentation-for-service-broker"></a>Где найти документацию по компоненту Service Broker?  
 Справочная документация по компоненту [!INCLUDE[ssSB](../../includes/sssb-md.md)] входит в документацию по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . В эту справочную документацию входят следующие разделы:  
  
-   См. информацию об инструкциях CREATE, ALTER и DROP в разделе [Инструкции на языке описания данных (DDL) (Transact-SQL)](/sql/odbc/reference/develop-app/ddl-statements)  
  
-   [Представления каталога компонента Service Broker (Transact-SQL)](/sql/relational-databases/system-catalog-views/service-broker-catalog-views-transact-sql)  
  
-   [Динамические административные представления, связанные с компонентом Service Broker (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql)  
  
-   [Программа ssbdiagnose (компонент Service Broker)](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
 Сведения об основных понятиях компонента [, а также задачах разработки и управления см. в](https://go.microsoft.com/fwlink/?LinkId=231312) ранее опубликованной документации [!INCLUDE[ssSB](../../includes/sssb-md.md)] . Эта документация не повторяется в документации по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] из-за малого числа изменений в компоненте [!INCLUDE[ssSB](../../includes/sssb-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="whats-new-in-service-broker"></a>Новые возможности (компонент Service Broker)  
 В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]не были внесены значимые изменения.  В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]появились следующие изменения.  
  
### <a name="messages-can-be-sent-to-multiple-target-services-multicast"></a>Сообщения могут отправляться в несколько целевых служб (многоадресная рассылка)  
 Синтаксис инструкции [SEND (Transact-SQL)](/sql/t-sql/statements/send-transact-sql) расширен для включения многоадресной рассылки благодаря поддержке нескольких дескрипторов диалога.  
  
### <a name="queues-expose-the-message-enqueued-time"></a>Очереди предоставляют время нахождения сообщения в очереди  
 Очереди содержат новый столбец **message_enqueue_time**, в котором показано время нахождения сообщения в очереди.  
  
### <a name="poison-message-handling-can-be-disabled"></a>Можно отключить обработку сообщений о сбое  
 Теперь в инструкциях [CREATE QUEUE (Transact-SQL)](/sql/t-sql/statements/create-queue-transact-sql) и [ALTER QUEUE (Transact-SQL)](/sql/t-sql/statements/alter-queue-transact-sql) можно включать или отключать обработку сообщений о сбое, добавляя предложение `POISON_MESSAGE_HANDLING (STATUS = ON | OFF)`. Представление каталога **sys.service_queues** теперь содержит столбец **is_poison_message_handling_enabled** , показывающий, включено ли сообщение об ошибке.  
  
### <a name="alwayson-support-in-service-broker"></a>Поддержка AlwaysOn в компоненте Service Broker  
 Дополнительные сведения см. в статье [Компонент Service Broker с группами доступности AlwaysOn (SQL Server)](../availability-groups/windows/service-broker-with-always-on-availability-groups-sql-server.md).  
  
  
