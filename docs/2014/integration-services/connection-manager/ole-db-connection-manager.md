---
title: Диспетчер подключений OLE DB | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- OLE DB connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], OLE DB
- connections [Integration Services], OLE DB
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7034c52fa3f05032d6fc4585f1baf171421d0ab2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48156714"
---
# <a name="ole-db-connection-manager"></a>диспетчер соединений OLE DB
  Диспетчер соединений OLE DB позволяет пакету подключаться к источнику данных с помощью поставщика OLE DB. Например, диспетчер соединений OLE DB, который подключается к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , может использовать поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Собственный поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 11.0 не поддерживает новые ключевые слова строки соединения (MultiSubnetFailover=True) для отказоустойчивых кластеров с несколькими подсетями. Дополнительные сведения см. в разделе [заметки о выпуске SQL Server](http://go.microsoft.com/fwlink/?LinkId=247824) и запись блога [Многоподсетевой отработки отказа AlwaysOn и SSIS](http://go.microsoft.com/fwlink/?LinkId=247825), на www.mattmasson.com.  
  
 Некоторые задачи служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и компоненты потока данных применяют диспетчер соединений OLE DB. Например, источник OLE DB и назначение «OLE DB» применяют диспетчер соединений для извлечения и загрузки данных, а задача «Выполнение SQL» может применять его для подключения к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы выполнять запросы.  
  
 Кроме того, диспетчер соединений OLE DB применяется для доступа к источникам данных OLE DB в пользовательских задачах, написанных неуправляемым кодом на языке, подобном C++.  
  
 При добавлении к пакету диспетчер соединений OLE DB [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер, который будет решать задачи соединений OLE DB во время выполнения, устанавливает свойства диспетчера соединений и добавляет диспетчер соединений для соединений `Connections` коллекции пакет.  
  
 `ConnectionManagerType` Свойства диспетчера соединений присваивается `OLEDB`.  
  
 Диспетчер соединений OLE DB можно настроить следующими способами:  
  
-   Укажите конкретную строку соединения, соответствующую требованиям конфигурации выбранного поставщика.  
  
-   В зависимости от поставщика предоставьте имя источника данных, к которому производится подключение.  
  
-   Предоставьте безопасные учетные данные, соответствующие выбранному поставщику.  
  
-   Обозначает, будет ли соединение, созданное из диспетчера соединений, сохранено во время выполнения.  
  
## <a name="logging"></a>Ведение журнала  
 В журнал можно записывать вызовы, сделанные диспетчером соединений OLE DB к внешним поставщикам данных. Эта возможность ведения журнала может быть использована для устранения неполадок соединений, которые выполняются диспетчером соединений OLE DB к внешним источникам данных. Чтобы вести журнал вызовов, которые диспетчер соединений OLE DB совершает к внешним поставщикам данных, необходимо включить ведение журнала пакета и выбрать событие **Диагностика** на уровне пакета. Дополнительные сведения см. в разделе [Инструменты устранения неполадок при выполнении пакетов](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## <a name="configuration-of-the-oledb-connection-manager"></a>Настройка диспетчера соединений OLE DB  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами. Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в разделе [Настройка диспетчера соединений OLE DB](../configure-ole-db-connection-manager.md). Дополнительные сведения о настройке диспетчера соединений программными средствами см. в документации по классу **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** в руководстве для разработчиков.  
  
## <a name="related-content"></a>См. также  
  
-   Статья Wiki [Соединители служб SSIS с Oracle](http://go.microsoft.com/fwlink/?LinkId=220670) на сайте social.technet.microsoft.com  
  
-   Техническая статья [Connection Strings for OLE DB Providers](http://go.microsoft.com/fwlink/?LinkId=220744)(Строки подключения для поставщиков OLE DB) на сайте carlprothman.net.  
  
## <a name="see-also"></a>См. также  
 [Источник OLE DB](../data-flow/ole-db-source.md)   
 [Назначение OLE DB](../data-flow/ole-db-destination.md)   
 [Задача "Выполнение SQL"](../control-flow/execute-sql-task.md)   
 [Службы Integration Services &#40;SSIS&#41; подключений](integration-services-ssis-connections.md)  
  
  
