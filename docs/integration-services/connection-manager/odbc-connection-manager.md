---
title: "Диспетчер соединений ODBC | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.dts.designer.odbcconnection.f1
helpviewer_keywords:
- connections [Integration Services], ODBC
- ODBC connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], ODBC
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
caps.latest.revision: "41"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 761957881888a7ab44b40c4562836d3dc11d0452
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="odbc-connection-manager"></a>диспетчер соединений ODBC
  Диспетчер соединений ODBC позволяет пакету подключаться к разнообразным системам управления базами данных, используя открытый интерфейс взаимодействия с базами данных (ODBC).  
  
 При добавлении соединения ODBC к пакету и задании свойств диспетчера соединений службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер соединений и добавляют его к коллекции **Connections** пакета. Во время выполнения диспетчер соединений рассматривается как физическое соединение с ODBC.  
  
 Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **ODBC**.  
  
 Настроить диспетчер соединений ODBC можно следующими способами:  
  
-   Предоставить строку соединения, которая ссылается на пользовательское или системное имя источника данных.  
  
-   Указать сервер, к которому нужно подключиться.  
  
-   Указать, сохранять ли соединение во время выполнения.  
  
## <a name="configuration-of-the-odbc-connection-manager"></a>Настройка диспетчера соединений ODBC  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в одном из последующих разделов.  
  
-   [Справочник по пользовательскому интерфейсу диспетчера соединений ODBC](../../integration-services/connection-manager/odbc-connection-manager-ui-reference.md)  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="odbc-connection-manager-ui-reference"></a>Справочник по пользовательскому интерфейсу диспетчера соединений ODBC
  Диалоговое окно **Настройка диспетчера соединений ODBC** используется для добавления соединения с источником данных ODBC.  
  
 Дополнительные сведения о диспетчере соединений ODBC см. в разделе [ODBC Connection Manager](../../integration-services/connection-manager/odbc-connection-manager.md).  
  
### <a name="options"></a>Параметры  
 **Подключения к данным**  
 Выберите из списка существующий диспетчер соединений ODBC.  
  
 **Свойства подключения к данным**  
 Просмотрите свойства и значения выбранного диспетчера соединений ODBC.  
  
 **Создать**  
 Создайте новый диспетчер соединений ODBC с помощью диалогового окна **Диспетчер соединений** . При необходимости это диалоговое окно также позволяет создать новый источник данных ODBC.  
  
 **Delete**  
 Выберите соединение и затем удалите его, используя кнопку **Удалить** .  
## <a name="see-also"></a>См. также:  
 [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
