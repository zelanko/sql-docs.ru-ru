---
title: Создание предупреждения для базы данных SQL Server | Документация Майкрософт
description: Вы можете использовать системный монитор для создания предупреждения базы данных SQL Server, которое будет выводиться, когда счетчик компонента системного монитора достигнет порогового значения.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
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
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 512c902e0b35e15b65866464500b4928e105d4ad
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96506044"
---
# <a name="create-a-sql-server-database-alert"></a>Создание предупреждения для базы данных SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Можно использовать системный монитор для создания предупреждения, которое будет выводиться, когда счетчик компонента System Monitor достигает порогового значения. В ответ на предупреждение системный монитор запускает приложение, такое как пользовательское приложение, созданное для обработки условий предупреждения. Например можно создать предупреждение, которое будет выводиться, когда число взаимоблокировок превысит заданное значение.  
  
 Предупреждения также могут задаваться при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в статье [Оповещения](../../ssms/agent/alerts.md).  
  
 Дополнительные сведения об использовании системного монитора для настройки предупреждения базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Настройка оповещения базы данных SQL Server (Windows)](../../relational-databases/performance/set-up-a-sql-server-database-alert-windows.md).  
  
## <a name="see-also"></a>См. также:  
 [sp_add_alert (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sys.sysperfinfo (Transact-SQL)](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  
