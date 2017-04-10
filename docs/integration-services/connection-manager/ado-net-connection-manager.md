---
title: "Диспетчер соединений ADO.NET | Microsoft Docs"
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
  - "диспетчеры подключений [службы Integration Services], ADO.NET"
  - "ADO.NET, диспетчер соединений [службы Integration Services]"
  - "подключения [службы Integration Services], ADO.NET"
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
caps.latest.revision: 59
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 59
---
# Диспетчер соединений ADO.NET
  Диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] позволяет пакету обращаться к источникам данных с помощью поставщика .NET. Чаще всего этот диспетчер используется для доступа к таким источникам данных, как [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также к источникам данных, предоставляемым посредством OLE DB и XML в пользовательских задачах, написанных на управляемом коде, например коде языка C#.  
  
 Если добавить к пакету диспетчер соединений служб [!INCLUDE[vstecado](../../includes/vstecado-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает диспетчер соединений, который будет во время выполнения определяться как соединение [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] со службами [!INCLUDE[vstecado](../../includes/vstecado-md.md)], устанавливает свойства диспетчера соединений и добавляет диспетчер соединений в коллекцию **Соединения** пакета.  
  
 Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **ADO.NET**. Значение **ConnectionManagerType** уточняется: в него включается имя поставщика .NET, используемого диспетчером соединений.  
  
## Устранение неполадок, связанных с диспетчером соединений ADO.NET  
 В журнал можно записывать вызовы, сделанные диспетчером соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] к внешним источникам данных. Эта возможность протоколирования может быть использована для устранения неполадок соединений, которые устанавливаются диспетчером соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] с внешними источниками данных. Чтобы протоколировать вызовы, которые диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] совершает к внешним поставщикам данных, необходимо разрешить ведение журнала пакета и выбрать событие **Диагностика** на уровне пакета. Дополнительные сведения см. в разделе [Инструменты устранения неполадок при выполнении пакетов](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
 При чтении данных диспетчером соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] данные определенных типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формируют результаты, показанные в следующей таблице.  
  
|Тип данных SQL Server|Результат|  
|--------------------------|------------|  
|**time**, **datetimeoffset**|Выполнение пакета завершается неудачей, если в пакете не используются параметризованные команды SQL. Чтобы применить параметризованные команды SQL, используйте в пакете задачу «Выполнение SQL». Дополнительные сведения см. в разделах [Задача "Выполнение SQL"](../../integration-services/control-flow/execute-sql-task.md) и [Параметры и коды возврата в задаче "Выполнение SQL"](../Topic/Parameters%20and%20Return%20Codes%20in%20the%20Execute%20SQL%20Task.md).|  
|**datetime2**|Диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] отбрасывает миллисекунды.|  
  
> [!NOTE]  
>  Дополнительные сведения о типах данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их сопоставлении с типами данных [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] см. в разделе [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md) и [Типы данных службы Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Настройка диспетчера соединений ADO.NET  
 Диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] можно настроить следующими способами:  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
-   Предоставьте специальную строку подключения, настроенную таким образом, чтобы удовлетворить требования выбранного поставщика .NET.  
  
-   В зависимости от поставщика предоставьте имя источника данных, к которому производится подключение.  
  
-   Предоставьте безопасные учетные данные, соответствующие выбранному поставщику.  
  
-   Обозначает, будет ли соединение, созданное из диспетчера соединений, сохранено во время выполнения.  
  
 Многие параметры конфигурации диспетчера соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] зависят от используемого им поставщика .NET.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в одном из последующих разделов.  
  
-   [настройка диспетчера соединений ADO.NET](../../integration-services/connection-manager/configure-ado-net-connection-manager.md)  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## См. также  
 [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  