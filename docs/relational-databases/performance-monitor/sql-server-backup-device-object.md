---
title: SQL Server, объект Backup Device | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 87cda19087f0e1ed742399032888a77f2a013dd4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85787344"
---
# <a name="sql-server-backup-device-object"></a>SQL Server, объект Backup Device
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **Устройство резервного копирования** предоставляет счетчики для контроля над устройствами резервного копирования и операциями восстановления Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Контролировать устройства резервного копирования нужно, если необходимо определить пропускную способность, состояние или производительность операций резервного копирования и восстановления для каждого из устройств. Чтобы контролировать пропускную способность операции резервного копирования или восстановить всю **базу данных**, используйте счетчик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Пропускная способность резервного копирования/восстановления в байтах/с**объекта**. Дополнительные сведения см. в статье [SQL Server, Databases Object](../../relational-databases/performance-monitor/sql-server-databases-object.md).  
  
 В следующей таблице описан счетчик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Устройство резервного копирования**.  
  
|Счетчики устройств резервного копирования SQL Server|Description|  
|---------------------------------------|-----------------|  
|**Пропускная способность устройства, байт/с**|Пропускная способность операций чтения и записи (в байтах на секунду) для устройства резервного копирования при создании резервной копии базы данных или ее восстановлении. Этот счетчик существует, только если выполняется операция резервного копирования или восстановления.|  
  
## <a name="see-also"></a>См. также:  
 [Устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
