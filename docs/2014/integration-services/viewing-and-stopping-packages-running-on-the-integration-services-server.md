---
title: Просмотр и остановка пакетов, выполняющихся на интеграцию сервера служб | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], managing
- managing running packages [Integration Services]
- packages [Integration Services], running
- running package [Integration Services], managing
ms.assetid: 11bf44e6-f6b0-475f-b816-40e914dbac80
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 993f5cc3cba13e9a7d2c6380f719d5e7b24ca0a1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140564"
---
# <a name="viewing-and-stopping-packages-running-on-the-integration-services-server"></a>Просмотр и остановка пакетов, выполняющихся на сервере служб Integration Services
  `SSISDB` Базы данных хранится журнал выполнения во внутренних таблицах, невидимых для пользователей. Однако сведения, которые она предоставляет, можно получить с помощью запросов к общим представлениям. Также она предоставляет хранимые процедуры, которые можно вызвать для выполнения стандартных задач, связанных с пакетами.  
  
 Обычно управление объектами служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сервере выполняется в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Но также можно создать запросы к представлениям базы данных и вызывать хранимые процедуры напрямую, либо написать специальный код, вызывающий управляемый API-интерфейс. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и управляемый API-Интерфейс запросы к представлениям и вызывать хранимые процедуры для выполнения многих своих задач. Например, можно просмотреть список пакетов служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , выполняющихся в данный момент на сервере, и запросить остановку их выполнения при необходимости.  
  
## <a name="viewing-the-list-of-running-packages"></a>Просмотр списка выполняемых пакетов  
 Можно просмотреть список пакетов, которые в данный момент выполняются на сервере, в диалоговом окне **Активные операции** . Дополнительные сведения см. в статье [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md).  
  
 Дополнительные сведения о других методах, которые можно использовать для просмотра списка запущенных пакетов, см. в следующих разделах.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] доступ  
 Чтобы просмотреть список пакетов, запущенных на сервере, создайте запрос к представлению [catalog.executions (база данных SSISDB)](/sql/integration-services/system-views/catalog-executions-ssisdb-database) для пакетов со значением состояния 2.  
  
 Программный доступ с использованием управляемого API-интерфейса  
 См. пространство имен <xref:Microsoft.SqlServer.Management.IntegrationServices> и его классы.  
  
## <a name="stopping-a-running-package"></a>Остановка выполнения пакета  
 Можно запросить остановку выполняющегося пакета в диалоговом окне **Активные операции** . Дополнительные сведения см. в статье [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md).  
  
 Дополнительные сведения о других методах, которые можно использовать для остановки запущенного пакета, см. в следующих разделах.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] доступ  
 Чтобы остановить выполняемый на сервере пакет, следует вызвать хранимую процедуру [catalog.stop_operation (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database).  
  
 Программный доступ с использованием управляемого API-интерфейса  
 См. пространство имен <xref:Microsoft.SqlServer.Management.IntegrationServices> и его классы.  
  
## <a name="viewing-the-history-of-packages-that-have-run"></a>Просмотр журнала выполненных пакетов  
 Для просмотра журнала пакетов, выполнявшихся в среде [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], используйте отчет **Все выполнения** . Дополнительные сведения об отчете **Все выполнения** и других стандартных отчетах см. в разделе [Отчеты для сервера служб Integration Services](../../2014/integration-services/reports-for-the-integration-services-server.md).  
  
 Сведения о других методах, которые можно использовать для просмотра журнала выполняющихся пакетов, см. в следующих разделах.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] доступ  
 Для просмотра сведений о выполнявшихся пакетах запросите представление [catalog.executions (база данных SSISDB)](/sql/integration-services/system-views/catalog-executions-ssisdb-database).  
  
 Программный доступ с использованием управляемого API-интерфейса  
 См. пространство имен <xref:Microsoft.SqlServer.Management.IntegrationServices> и его классы.  
  
## <a name="see-also"></a>См. также  
 [Запуск проектов и пакетов](packages/run-integration-services-ssis-packages.md)   
 [Отчеты по устранению неполадок для выполнения пакетов](troubleshooting/troubleshooting-reports-for-package-execution.md)  
  
  
