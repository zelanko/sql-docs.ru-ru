---
title: Диспетчер соединений ODBC | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.odbcconnection.f1
helpviewer_keywords:
- connections [Integration Services], ODBC
- ODBC connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], ODBC
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 4a9b8fa4b316c34bb2cfc4b51c0fcb6ba310367e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68104029"
---
# <a name="odbc-connection-manager"></a>диспетчер соединений ODBC

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
  
-   [Справочник по пользовательскому интерфейсу диспетчера подключений ODBC](../../integration-services/connection-manager/odbc-connection-manager-ui-reference.md)  
  
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
  
 **Удаление**  
 Выберите соединение и затем удалите его, используя кнопку **Удалить** .  
## <a name="see-also"></a>См. также:  
 [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
