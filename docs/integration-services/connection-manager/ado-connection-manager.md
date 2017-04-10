---
title: "Диспетчер соединений ADO | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "подключения [службы Integration Services], ADO"
  - "диспетчеры подключений [службы Integration Services], ADO"
  - "диспетчер соединений ADO [службы Integration Services]"
ms.assetid: 490418bc-5ef1-41b8-a9c8-de38aa96e0f6
caps.latest.revision: 54
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 54
---
# Диспетчер соединений ADO
  Диспетчер соединений ADO позволяет пакету подключаться к таким объектам ADO, как набор записей. Текущий диспетчер соединений обычно используется в пользовательских задачах, созданных в ранних версиях таких языков, как Microsoft Visual Basic 6.0, или в пользовательских задачах, которые являются частью существующего приложения, использующего ADO для подключения к источникам данных.  
  
 При добавлении к пакету диспетчера соединений ADO службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создают диспетчер соединений, который во время выполнения разрешается в соединение ADO, устанавливают свойства диспетчера соединений и добавляют диспетчер соединений в коллекцию **Соединения** пакета. Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **ADO**.  
  
## Устранение неполадок диспетчера соединений ADO  
 При считывании данных диспетчером соединений ADO некоторые типы данных даты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формируют результаты, показанные в следующей таблице.  
  
|Тип данных SQL Server|Результат|  
|--------------------------|------------|  
|**time**, **datetimeoffset**|Выполнение пакета завершается неудачей, если в пакете не используются параметризованные команды SQL. Чтобы применить параметризованные команды SQL, используйте в пакете задачу «Выполнение SQL». Дополнительные сведения см. в разделах [Задача "Выполнение SQL"](../../integration-services/control-flow/execute-sql-task.md) и [Параметры и коды возврата в задаче "Выполнение SQL"](../Topic/Parameters%20and%20Return%20Codes%20in%20the%20Execute%20SQL%20Task.md).|  
|**datetime2**|Диспетчер соединений ADO усекает значение миллисекунд.|  
  
> [!NOTE]  
>  Дополнительные сведения о типах данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их сопоставлении с типами данных [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] см. в разделе [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md) и [Типы данных службы Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Настройка диспетчера соединений ADO  
 Настройку диспетчера соединений ADO можно осуществлять следующими способами.  
  
-   Укажите конкретную строку соединения, соответствующую требованиям конфигурации выбранного поставщика.  
  
-   В зависимости от поставщика предоставьте имя источника данных, к которому производится подключение.  
  
-   Предоставьте безопасные учетные данные, соответствующие выбранному поставщику.  
  
-   Обозначает, будет ли соединение, созданное из диспетчера соединений, сохранено во время выполнения.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [настройка диспетчера соединений OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## См. также  
 [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  