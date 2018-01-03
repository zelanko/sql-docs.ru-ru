---
title: "Свойства браузера SQL Server (вкладка «Дополнительно») | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba79137a-cb72-4bf3-a650-e11d02cfce10
caps.latest.revision: "19"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 86d92925849a68075adcce8054a4c9354acc7eca
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sql-server-browser-properties-advanced-tab"></a>Свойства браузера SQL Server (вкладка «Дополнительно»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Браузер запускается как служба на сервере. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает входящие запросы к ресурсам [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и предоставляет сведения об экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , установленных на компьютере.  
  
## <a name="options"></a>Параметры  
 **Кластеризованный**  
 Указывает, установлена ли эта служба в качестве ресурса кластеризованного сервера.  
  
 **Передача отзывов пользователей**  
 Указывает, был ли запущен контроль качества обслуживания для этой службы. Дополнительные сведения о передаче отзывов пользователей см. в разделе «Настройки параметров отчета об ошибках» электронной документации.  
  
 **Каталог дампа**  
 Каталог, куда в случае возникновения ошибки помещаются дампы памяти.  
  
 **Отчет об ошибках**  
 Если установлено значение **Да**, то в случае возникновения серьезного сбоя программа "Доктор Ватсон» направит сведения либо в [!INCLUDE[msCoName](../../includes/msconame-md.md)], либо на сервер ошибок. Дополнительные сведения по отчетам об ошибках см. в разделе «Настройки параметров отчета об ошибках» электронной документации.  
  
 **Идентификатор экземпляра**  
 Указывает экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который использует этот экземпляр агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Экземпляр по умолчанию: **MSSQL10_50.MSSQLSERVER**.  
  
## <a name="see-also"></a>См. также:  
 [Служба обозревателя SQL Server](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
