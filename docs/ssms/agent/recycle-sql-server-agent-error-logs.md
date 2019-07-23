---
title: Очистка журналов ошибок агента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 822ce1ba69c1fafb4e09281f4c436e3d1cc760ea
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266802"
---
# <a name="recycle-sql-server-agent-error-logs"></a>Очистка журналов ошибок агента SQL Server
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Эта страница позволяет очистить журналы ошибок агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Очистка журнала закрывает текущий журнал ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и начинает новый журнал ошибок без перезапуска службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Учтите, что агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит девять самых последних журналов ошибок. Если в наличии все девять журналов, при очистке журнала ошибок агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удаляет самый старый журнал.  
  
## <a name="see-also"></a>См. также:  
[Журнал ошибок агента SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  
