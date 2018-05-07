---
title: Свойства агента браузера SQL Server (вкладка "Дополнительно") | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ba79137a-cb72-4bf3-a650-e11d02cfce10
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cb9f67a25adf9192dbdf896766d9a98a4ce49074
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-browser-properties-advanced-tab"></a>Свойства браузера SQL Server (вкладка «Дополнительно»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Программа браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает в качестве службы на сервере. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает входящие запросы к ресурсам [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и предоставляет сведения об экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , установленных на компьютере.  
  
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
  
  
