---
title: Настройка параметра конфигурации сервера remote data archive | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b5817b5a-f39a-4faf-b11e-a47b54fd9f32
author: rothja
ms.author: jroth
manager: jroth
ms.openlocfilehash: 39967c68efa3f514759c3c7c910674f62097e3ce
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66783861"
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
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
