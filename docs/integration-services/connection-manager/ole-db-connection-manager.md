---
title: Диспетчер подключений OLE DB | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: connection-manager
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.oledbconnection.f1
helpviewer_keywords:
- OLE DB connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], OLE DB
- connections [Integration Services], OLE DB
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a65995d0e4f36cd1e330c01345834d1bca68b948
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-connection-manager"></a>диспетчер соединений OLE DB
  Диспетчер соединений OLE DB позволяет пакету подключаться к источнику данных с помощью поставщика OLE DB. Например, диспетчер соединений OLE DB, который подключается к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , может использовать поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].    
    
> [!NOTE]    
>  Собственный поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 11.0 не поддерживает новые ключевые слова строки соединения (MultiSubnetFailover=True) для отказоустойчивых кластеров с несколькими подсетями. Дополнительные сведения см. в разделе [Заметки о выпуске SQL Server](http://go.microsoft.com/fwlink/?LinkId=247824) и запись блога [Always On Multi-Subnet Failover and SSIS](http://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/)(Отработка отказа в нескольких подсетях и службы SSIS) на сайте www.mattmasson.com.    
    
> [!NOTE]    
>  Если источником данных является [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007 или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007, то для него понадобится источник данных, отличный от поставщиков для более ранних версий Excel или Access. Дополнительные сведения см. в разделе [Подключение к книге Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md) и [Подключение к базе данных Access](../../integration-services/connection-manager/connect-to-an-access-database.md).    
    
 Некоторые задачи служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и компоненты потока данных применяют диспетчер соединений OLE DB. Например, источник OLE DB и назначение «OLE DB» применяют диспетчер соединений для извлечения и загрузки данных, а задача «Выполнение SQL» может применять его для подключения к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы выполнять запросы.    
    
 Кроме того, диспетчер соединений OLE DB применяется для доступа к источникам данных OLE DB в пользовательских задачах, написанных неуправляемым кодом на языке, подобном C++.    
    
 При добавлении к пакету диспетчера соединений OLE DB службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер соединений, который будет решать задачи соединений OLE DB во время выполнения, устанавливает свойства диспетчера соединений и добавляет его к коллекции **Connections** пакета.    
    
 Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **OLEDB**.    
    
 Диспетчер соединений OLE DB можно настроить следующими способами:    
    
-   Укажите конкретную строку соединения, соответствующую требованиям конфигурации выбранного поставщика.    
    
-   В зависимости от поставщика предоставьте имя источника данных, к которому производится подключение.    
    
-   Предоставьте безопасные учетные данные, соответствующие выбранному поставщику.    
    
-   Обозначает, будет ли соединение, созданное из диспетчера соединений, сохранено во время выполнения.    
    
## <a name="logging"></a>Ведение журнала    
 В журнал можно записывать вызовы, сделанные диспетчером соединений OLE DB к внешним поставщикам данных. Эта возможность ведения журнала может быть использована для устранения неполадок соединений, которые выполняются диспетчером соединений OLE DB к внешним источникам данных. Чтобы вести журнал вызовов, которые диспетчер соединений OLE DB совершает к внешним поставщикам данных, необходимо включить ведение журнала пакета и выбрать событие **Диагностика** на уровне пакета. Дополнительные сведения см. в разделе [Инструменты устранения неполадок при выполнении пакетов](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).    
    
## <a name="configuration-of-the-oledb-connection-manager"></a>Настройка диспетчера соединений OLE DB    
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами. Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в разделе [Настройка диспетчера соединений OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md). Дополнительные сведения о настройке диспетчера соединений программными средствами см. в документации по классу **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** в руководстве для разработчиков.    
    
## <a name="related-content"></a>См. также    
    
-   Статья Wiki [Соединители служб SSIS с Oracle](http://go.microsoft.com/fwlink/?LinkId=220670) на сайте social.technet.microsoft.com    
    
-   Техническая статья [Connection Strings for OLE DB Providers](http://go.microsoft.com/fwlink/?LinkId=220744)(Строки подключения для поставщиков OLE DB) на сайте carlprothman.net.    
    
## <a name="configure-ole-db-connection-manager"></a>настройка диспетчера соединений OLE DB
  Используйте диалоговое окно **Настройка диспетчера соединений OLE DB** , чтобы добавить соединение с источником данных. Это может быть либо новое соединение, либо копия существующего соединения.  
  
> [!NOTE]  
>  Для источника данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007 потребуется поставщик данных, отличный от того, который использовался в предыдущих версиях Excel. Дополнительные сведения см. в разделе [Подключение к книге Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md).  
>   
>  Если источником данных является [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007, то для него понадобится поставщик OLE DB, отличающийся от поставщиков для более ранних версий Access. Дополнительные сведения см. в разделе [Подключение к базе данных Access](../../integration-services/connection-manager/connect-to-an-access-database.md).  
  
 Дополнительные сведения о диспетчере соединений OLE DB см. в разделе [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
### <a name="options"></a>Параметры  
 **Подключения к данным**  
 Выберите из списка существующее подключение к данным OLE DB.  
  
 **Свойства подключения к данным**  
 Просмотрите свойства и значения выбранного подключения к данным OLE DB.  
  
 **Создать**  
 Создайте подключение к данным OLE DB с помощью диалогового окна **Диспетчер соединений** .  
  
 **Удаление**  
 Выберите подключение к данным и удалите его с помощью кнопки **Удалить** .  
  
## <a name="see-also"></a>См. также:    
 [Источник OLE DB](../../integration-services/data-flow/ole-db-source.md)     
 [Назначение OLE DB](../../integration-services/data-flow/ole-db-destination.md)     
 [Задача "Выполнение SQL"](../../integration-services/control-flow/execute-sql-task.md)     
 [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md)    
    
  
