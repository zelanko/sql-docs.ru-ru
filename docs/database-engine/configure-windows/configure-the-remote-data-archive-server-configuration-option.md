---
title: Настройка параметра конфигурации сервера remote data archive | Документы Майкрософт
description: Сведения о том, как использовать параметр remote data archive в SQL Server, чтобы указать, разрешено ли включать Stretch для баз данных и таблиц на сервере.
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
ms.openlocfilehash: fc53b5392d6bd493b634e9e2c8a4a92613eb8c32
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785752"
---
# <a name="configure-the-remote-data-archive-server-configuration-option"></a>Настройка параметра конфигурации сервера remote data archive
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
 [Включение Stretch Database для базы данных](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
