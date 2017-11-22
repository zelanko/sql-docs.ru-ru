---
title: "Настройка параметра конфигурации сервера remote data archive | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5817b5a-f39a-4faf-b11e-a47b54fd9f32
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0644ac41ab6157ee658935e0a41d545096f3be48
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="configure-the-remote-data-archive-server-configuration-option"></a>Настройка параметра конфигурации сервера remote data archive
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  С помощью параметра **remote data archive** можно указать, разрешено ли включать Stretch для баз данных и таблиц на сервере. Дополнительные сведения см. в разделе [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
 Параметр **remote data archive** может иметь следующие значения:  
  
|Значение|Описание|  
|-----------|-----------------|  
|0|Stretch нельзя использовать для баз данных и таблиц на сервере.|  
|1|Stretch можно использовать для баз данных и таблиц на сервере.|  
  
 Чтобы выполнить **sp_configure** для присвоения значения параметру **remote data archive** , необходимо иметь разрешения sysadmin или serveradmin.  
  
## <a name="example"></a>Пример  
 В приведенном ниже примере сначала выводится текущее значение параметра **remote data archive** . Затем включается параметр **remote data archive** путем изменения его значения на 1.  
  
```  
EXEC sp_configure 'remote data archive';  
GO  
EXEC sp_configure 'remote data archive' , '1';  
GO  
RECONFIGURE;  
GO  
```  
  
 Чтобы отключить этот параметр, задайте значение 0.  
  
## <a name="see-also"></a>См. также:  
 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [База данных Stretch](../../sql-server/stretch-database/stretch-database.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
