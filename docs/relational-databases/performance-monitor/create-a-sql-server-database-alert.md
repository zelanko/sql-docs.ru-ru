---
title: Создание предупреждения для базы данных SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], alerts
- alerts [SQL Server], creating
- thresholds [SQL Server]
- database alerts [SQL Server]
- tuning databases [SQL Server], alerts
- monitoring performance [SQL Server], alerts
- monitoring server performance [SQL Server], alerts
- database monitoring [SQL Server], alerts
- server performance [SQL Server], alerts
ms.assetid: 0511136a-1b6b-4095-aa45-39e77b67aba2
caps.latest.revision: 22
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4b365f6e1272e413ab46035e3f093697fd7adaa8
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40411084"
---
# <a name="create-a-sql-server-database-alert"></a>Создание предупреждения для базы данных SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Можно использовать системный монитор для создания предупреждения, которое будет выводиться, когда счетчик компонента System Monitor достигает порогового значения. В ответ на предупреждение системный монитор запускает приложение, такое как пользовательское приложение, созданное для обработки условий предупреждения. Например можно создать предупреждение, которое будет выводиться, когда число взаимоблокировок превысит заданное значение.  
  
 Предупреждения также могут задаваться при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в статье [Предупреждения](../../ssms/agent/alerts.md).  
  
 Дополнительные сведения об использовании системного монитора для настройки предупреждения базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Настройка оповещения базы данных SQL Server (Windows)](../../relational-databases/performance/set-up-a-sql-server-database-alert-windows.md).  
  
## <a name="see-also"></a>См. также:  
 [sp_add_alert (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sys.sysperfinfo (Transact-SQL)](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  
