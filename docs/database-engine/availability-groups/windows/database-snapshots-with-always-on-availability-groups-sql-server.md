---
title: "Моментальные снимки баз данных для групп доступности AlwaysOn (SQL Server) | Документы Майкрософт"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database snapshots [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 7432da1c-ce2f-4cd9-af41-54c97744166b
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a490cf9ff2ed4b847525056411cc58923e03e97f
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="database-snapshots-with-always-on-availability-groups-sql-server"></a>Моментальные снимки баз данных для групп доступности AlwaysOn (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Моментальный снимок базы данных можно создать в базе данных-источнике или базе данных-получателе в группе доступности. Ролью реплики должна быть PRIMARY или SECONDARY, она не может находиться в состоянии RESOLVING.  
  
 Для создания моментального снимка рекомендуется, чтобы состояние синхронизации базы данных было SYNCHRONIZING или SYNCHRONIZED. Однако моментальные снимки базы данных могут создаваться и в состоянии синхронизации базы данных NOT SYNCHRONIZING.  
  
 Моментальный снимок базы данных дополнительной реплики должен продолжить работу в случае, если она находится в состоянии DISCONNECTED от основной реплики.  
  
 Некоторые условия [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] могут вызвать перезапуск как базы данных-источника, так и ее моментальных снимков базы данных, вызвав временное отключение пользователей. Ниже приведены эти условия.  
  
-   Основная реплика изменяет роли либо из-за того, что текущая основная реплика отключается и снова включается на том же экземпляра сервера, либо из-за того, что группа доступности выполнила переход на другой ресурс.  
  
-   База данных переходит в роль получателя.  
  
 Если реплика доступности, на которой размещен моментальный снимок базы данных, выполнила переход на другой ресурс, моментальные снимки базы данных остаются на экземпляре сервера, где они были созданы. Эти снимки будут доступны пользователям и после перехода на другой ресурс. Если для вашей среды важна производительность, рекомендуется создавать моментальные снимки баз данных только в базах данных-получателях, размещенных в дополнительной реплике, настроенной на режим ручного перехода на другой ресурс.  Если потребуется вручную перевести группу доступности на другой ресурс в данной дополнительной реплике, можно будет создать новый набор моментальных снимков базы данных в другой дополнительной реплике, перенаправить клиентов к новым моментальным снимкам базы данных, а затем удалить все моментальные снимки баз данных, ставших базами данных-источниками.  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Моментальные снимки базы данных (SQL Server)](../../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  

