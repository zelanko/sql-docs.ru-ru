---
title: Очистка журналов ошибок агента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e966fcf544ace7a719d4760c366c69fe91b892f5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087980"
---
# <a name="recycle-sql-server-agent-error-logs"></a>Очистка журналов ошибок агента SQL Server
  Эта страница позволяет очистить журналы ошибок агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Очистка журнала закрывает текущий журнал ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и начинает новый журнал ошибок без перезапуска службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Учтите, что агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит девять самых последних журналов ошибок. Если в наличии все девять журналов, при очистке журнала ошибок агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удаляет самый старый журнал.  
  
## <a name="see-also"></a>См. также  
 [Журнал ошибок агента SQL Server](sql-server-agent-error-log.md)  
  
  