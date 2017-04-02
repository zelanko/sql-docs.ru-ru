---
title: "Параметр конфигурации сервера &#171;Ole Automation Procedures&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ole Automation Procedures, параметр"
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Параметр конфигурации сервера &#171;Ole Automation Procedures&#187;
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  C помощью параметра **Ole Automation Procedures** можно указать возможность создания экземпляров объектов OLE-автоматизации в пакетах [!INCLUDE[tsql](../../includes/tsql-md.md)]. Этот параметр также можно настроить с помощью управления на основе политики или с помощью хранимой процедуры **sp_configure**. Дополнительные сведения см. в разделе [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
 Параметр **Ole Automation Procedures** может принимать следующие значения:  
  
 0  
 Процедуры OLE-автоматизации отключены. По умолчанию для новых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 1  
 Процедуры OLE-автоматизации включены.  
  
 После включения процедур OLE-автоматизации процедура **sp_OACreate** запустит общую среду выполнения OLE.  
  
 Текущее значение параметра **Ole Automation Procedures** можно просмотреть и изменить с помощью системной хранимой процедуры **sp_configure**.  
  
## Примеры  
 В следующем примере показан просмотр текущего значения параметра OLE Automation procedures.  
  
```  
EXEC sp_configure 'Ole Automation Procedures';  
GO  
```  
  
 В следующем примере показано включение процедур OLE-автоматизации.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Ole Automation Procedures', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## См. также:  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Настройка контактной зоны](../../relational-databases/security/surface-area-configuration.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  