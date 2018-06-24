---
title: Диспетчер подключений ADO.NET | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection managers [Integration Services], ADO.NET
- ADO.NET connection manager [Integration Services]
- connections [Integration Services], ADO.NET
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 44b07e26877a4d53d87cabb2ce48894f067a2802
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36203871"
---
# <a name="adonet-connection-manager"></a>Диспетчер соединений ADO.NET
  Диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] позволяет пакету обращаться к источникам данных с помощью поставщика .NET. Чаще всего этот диспетчер используется для доступа к таким источникам данных, как [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также к источникам данных, предоставляемым посредством OLE DB и XML в пользовательских задачах, написанных на управляемом коде, например коде языка C#.  
  
 При добавлении [!INCLUDE[vstecado](../../includes/vstecado-md.md)] диспетчера соединений в пакет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает соединение диспетчер, который разрешается как [!INCLUDE[vstecado](../../includes/vstecado-md.md)] подключения во время выполнения, устанавливает свойства диспетчера соединений и добавляет диспетчер соединений `Connections` коллекцию пакета.  
  
 `ConnectionManagerType` Диспетчера соединений задано значение `ADO.NET`. Значение `ConnectionManagerType` является полное имя поставщика .NET, который использует диспетчер соединений.  
  
## <a name="adonet-connection-manager-troubleshooting"></a>Устранение неполадок, связанных с диспетчером соединений ADO.NET  
 В журнал можно записывать вызовы, сделанные диспетчером соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] к внешним источникам данных. Эта возможность протоколирования может быть использована для устранения неполадок соединений, которые устанавливаются диспетчером соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] с внешними источниками данных. Чтобы протоколировать вызовы, которые диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] совершает к внешним поставщикам данных, необходимо разрешить ведение журнала пакета и выбрать событие **Диагностика** на уровне пакета. Дополнительные сведения см. в разделе [Инструменты устранения неполадок при выполнении пакетов](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
 При чтении данных диспетчером соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] данные определенных типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формируют результаты, показанные в следующей таблице.  
  
|Тип данных SQL Server|Результат|  
|--------------------------|------------|  
|`time`, `datetimeoffset`|Выполнение пакета завершается неудачей, если в пакете не используются параметризованные команды SQL. Чтобы применить параметризованные команды SQL, используйте в пакете задачу «Выполнение SQL». Дополнительные сведения см. в разделах [Задача "Выполнение SQL"](../control-flow/execute-sql-task.md) и [Параметры и коды возврата в задаче "Выполнение SQL"](../parameters-and-return-codes-in-the-execute-sql-task.md).|  
|`datetime2`|Диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] отбрасывает миллисекунды.|  
  
> [!NOTE]  
>  Дополнительные сведения о типах данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их сопоставлении с типами данных [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] см. в разделе [Типы данных (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql) и [Типы данных службы Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="adonet-connection-manager-configuration"></a>Настройка диспетчера соединений ADO.NET  
 Диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] можно настроить следующими способами:  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
-   Предоставьте специальную строку подключения, настроенную таким образом, чтобы удовлетворить требования выбранного поставщика .NET.  
  
-   В зависимости от поставщика предоставьте имя источника данных, к которому производится подключение.  
  
-   Предоставьте безопасные учетные данные, соответствующие выбранному поставщику.  
  
-   Обозначает, будет ли соединение, созданное из диспетчера соединений, сохранено во время выполнения.  
  
 Многие параметры конфигурации диспетчера соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] зависят от используемого им поставщика .NET.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , см. в одном из последующих разделов.  
  
-   [Настройка диспетчера подключений ADO.NET](../configure-ado-net-connection-manager.md)  
  
 Сведения о программной настройке диспетчера соединений см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>См. также  
 [Службы Integration Services &#40;SSIS&#41; подключений](integration-services-ssis-connections.md)  
  
  
