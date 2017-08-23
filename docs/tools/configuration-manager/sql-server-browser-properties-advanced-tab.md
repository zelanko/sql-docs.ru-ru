---
title: "Свойства браузера SQL Server (вкладка «Дополнительно») | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba79137a-cb72-4bf3-a650-e11d02cfce10
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5f4c4d860ae086b8dd649bc74db8ed4ae3cf4fd1
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="sql-server-browser-properties-advanced-tab"></a>Свойства браузера SQL Server (вкладка «Дополнительно»)
  Программа браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает в качестве службы на сервере. Браузер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает входящие запросы к ресурсам [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и предоставляет сведения об экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], установленных на компьютере.  
  
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
  
## <a name="see-also"></a>См. также  
 [Служба обозревателя SQL Server](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
