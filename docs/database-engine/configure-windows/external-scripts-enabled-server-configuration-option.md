---
title: "Параметр конфигурации сервера external scripts enabled | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "external scripts enabled"
  - "external_scripts_enabled_TSQL"
helpviewer_keywords: 
  - "параметр external scripts enabled"
ms.assetid: 9d0ce165-8719-4007-9ae8-00f85cab3a0d
caps.latest.revision: 9
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 8
---
# Параметр конфигурации сервера external scripts enabled
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Параметр **external scripts enabled** позволяет включить выполнение скриптов с некоторыми удаленными расширениями языка. По умолчанию это свойство отключено (OFF). Программа установки может при необходимости задать этому свойству значение true, если установлены **расширенные службы аналитики**.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (от [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 Параметр external scripts enabled необходимо включить перед выполнением внешнего скрипта с помощью процедуры **sp_execute_external_script**. Процедура **sp_execute_external_script** служит для выполнения сценариев, написанных на поддерживаемом языке, например R. В версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] службы [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] включают в себя серверный компонент, устанавливаемый с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], а также набор инструментов рабочей станции и библиотек подключений, которые позволяют специалистам по анализу и обработке данных подключаться к высокопроизводительной среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Установите компонент **Расширения углубленной аналитики** в ходе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы включить выполнение скриптов R. Дополнительные сведения см. в разделе [Installing Previous Versions of SQL Server R Services](../Topic/Installing%20Previous%20Versions%20of%20SQL%20Server%20R%20Services.md).  
  
 Выполните следующий скрипт для включения внешних скриптов.  
  
```  
sp_configure 'external scripts enabled', 1;  
RECONFIGURE;  
```  
  
 Чтобы это изменение вступило в силу, необходимо перезапустить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## См. также:  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)   
 [Службы R SQL Server](../../advanced-analytics/r-services/sql-server-r-services.md)  
  
  