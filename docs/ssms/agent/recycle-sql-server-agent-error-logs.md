---
title: "Очистка журналов ошибок агента SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6b3b79686cbc194eda76fd1f4873d81c26d8d31c
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="recycle-sql-server-agent-error-logs"></a>Очистка журналов ошибок агента SQL Server
Эта страница позволяет очистить журналы ошибок агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Очистка журнала закрывает текущий журнал ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и начинает новый журнал ошибок без перезапуска службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Учтите, что агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] содержит девять самых последних журналов ошибок. Если в наличии все девять журналов, при очистке журнала ошибок агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] удаляет самый старый журнал.  
  
## <a name="see-also"></a>См. также:  
[Журнал ошибок агента SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  

