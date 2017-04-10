---
title: "Настройка параметра конфигурации сервера remote data archive | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5817b5a-f39a-4faf-b11e-a47b54fd9f32
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Настройка параметра конфигурации сервера remote data archive
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  С помощью параметра **remote data archive** можно указать, разрешено ли включать Stretch для баз данных и таблиц на сервере. Дополнительные сведения см. в разделе [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
 Параметр **remote data archive** может иметь следующие значения:  
  
|Значение|Описание|  
|-----------|-----------------|  
|0|Stretch нельзя использовать для баз данных и таблиц на сервере.|  
|1|Stretch можно использовать для баз данных и таблиц на сервере.|  
  
 Чтобы выполнить **sp_configure** для присвоения значения параметру **remote data archive**, необходимо иметь разрешения sysadmin или serveradmin.  
  
## Пример  
 В приведенном ниже примере сначала выводится текущее значение параметра **remote data archive**. Затем включается параметр **remote data archive** путем изменения его значения на 1.  
  
```  
EXEC sp_configure 'remote data archive';  
GO  
EXEC sp_configure 'remote data archive' , '1';  
GO  
RECONFIGURE;  
GO  
```  
  
 Чтобы отключить этот параметр, задайте значение 0.  
  
## См. также:  
 [Включение базы данных Stretch для базы данных](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [База данных Stretch](../../sql-server/stretch-database/stretch-database.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  