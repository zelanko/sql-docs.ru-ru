---
title: "Установка интервала опроса на целевых серверах | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interval for polling [SQL Server]
- target servers [SQL Server], polling interval
- polling interval [SQL Server]
ms.assetid: 4ffbbefa-77fb-442e-a77c-cb8c6cab9f3c
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 55865e4b4a2a112f92f58e229ccff74e5dd2a48d
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="set-the-polling-interval-for-target-servers"></a>Set the Polling Interval for Target Servers
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом разделе описывается установка частоты, с которой агент [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обновляет данные с главного сервера на целевых серверах. Задание — это указанная последовательность действий, выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Многосерверное задание — это задание, которое главный сервер выполняет на одном или нескольких целевых серверах.  
  
-   **Перед началом работы:**  [безопасность](#Security)  
  
-   **Установка интервала опроса на целевых серверах с использованием следующих средств:** [SQL Server Management Studio](#SSMS), [Transact-SQL](#TSQL)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
На каждом целевом сервере может одновременно выполняться только один экземпляр одного и того же задания. Каждый целевой сервер периодически опрашивает главный сервер, загружает копию новых назначенных ему заданий и отключается. Целевой сервер выполняет задание локально, а затем снова подключается к главному серверу, чтобы передать результирующее состояние задания.  
  
> [!NOTE]  
> Если главный сервер недоступен в момент, когда целевой сервер пытается передать состояние задания, то сведения о состоянии задания помещаются в очередь, пока главный сервер не станет доступен.  
  
### <a name="Security"></a>безопасность  
Дополнительные сведения см. в разделах [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md) и [Choose the Right SQL Server Agent Service Account for Multiserver Environments](../../ssms/agent/choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
**Установка интервала опроса на целевых серверах**  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**, укажите пункт **Администрирование нескольких серверов**, а затем выберите пункт **Управление целевыми серверами**.  
  
3.  На вкладке **Состояние целевого сервера** выберите **Разместить инструкции**.  
  
4.  В списке **Тип инструкции** выберите **Установить интервал опроса**.  
  
5.  В диалоговом окне **Интервал опроса** введите количество секунд от 10 до 28 800, которое должно пройти до того, как целевой сервер начнет опрос главного сервера.  
  
6.  В пункте **Адресаты**выполните одно из следующих действий:  
  
    1.  Выберите пункт **Все целевые серверы** , если они имеют общий интервал опроса.  
  
    2.  Выберите пункт **Эти целевые серверы** , если не все серверы имеют общий интервал опроса, и выберите каждый целевой сервер, который будет использовать указанный интервал.  
  
## <a name="TSQL"></a>Использование Transact-SQL  
**Установка интервала опроса на целевых серверах**  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента Database Engine и разверните его.  
  
2.  На панели инструментов нажмите кнопку **Создать запрос**.  
  
3.  В окне запроса используйте системную хранимую процедуру [sp_post_msx_operation (Transact-SQL)](http://msdn.microsoft.com/en-us/085deef8-2709-4da9-bb97-9ab32effdacf) , чтобы задать интервал опроса для целевых серверов.  
  
## <a name="see-also"></a>См. также:  
[sysdownloadlist](http://msdn.microsoft.com/en-us/71087a4c-e829-488e-aa7d-a9476e2b4779)  
  
