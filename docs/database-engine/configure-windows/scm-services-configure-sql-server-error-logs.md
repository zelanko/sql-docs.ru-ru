---
title: Настройка журналов ошибок SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: configure-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
caps.latest.revision: 18
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 35ac1dec7d7eaa65d719481dd67a663a802febf5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="scm-services---configure-sql-server-error-logs"></a>Службы SCM. Настройка журналов ошибок SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описано, как просмотреть и изменить способ очистки журналов ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>Открытие диалогового окна «Настройка журналов ошибок SQL Server»  
  
1.  В обозревателе объектов разверните экземпляр SQL Server, раскройте узел **Управление**, щелкните правой кнопкой мыши **Журналы SQL Server**, а затем выберите пункт **Настройка**.  
  
2.  В диалоговом окне **Настройка журналов ошибок SQL Server** выберите один из следующих параметров.  
  
     **Ограничить количество файлов журнала ошибок перед очисткой**  
     Установите этот флажок, чтобы ограничить количество файлов журнала ошибок, создаваемых до их очистки. При каждом запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создается новый журнал ошибок. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет резервные копии шести предыдущих журналов, если этот флажок не установлен и ниже не указано иное максимальное число файлов журнала ошибок.  
  
     **Максимальное количество файлов журналов ошибок**  
     Укажите максимальное количество файлов журнала ошибок, создаваемых до их очистки. Значение по умолчанию — 6, то есть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет шесть предыдущих резервных копий журналов до их очистки.  
  
  
