---
description: Set the Polling Interval for Target Servers
title: Set the Polling Interval for Target Servers
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- interval for polling [SQL Server]
- target servers [SQL Server], polling interval
- polling interval [SQL Server]
ms.assetid: 4ffbbefa-77fb-442e-a77c-cb8c6cab9f3c
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 9ae0186143d0bf3d9fff36d9d26a04f1cab0203f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88418050"
---
# <a name="set-the-polling-interval-for-target-servers"></a>Set the Polling Interval for Target Servers
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этой статье описано, как задать частоту, с которой агент [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обновляет данные с главного сервера на целевых серверах. Задание — это указанная последовательность действий, выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Многосерверное задание — это задание, которое главный сервер выполняет на одном или нескольких целевых серверах.  
  
-   **Перед началом работы**  [Безопасность](#Security)  
  
-   **Установка интервала опроса на целевых серверах с использованием следующих средств:** [SQL Server Management Studio](#SSMS), [Transact-SQL](#TSQL)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Перед началом  
На каждом целевом сервере может одновременно выполняться только один экземпляр одного и того же задания. Каждый целевой сервер периодически опрашивает главный сервер, загружает копию новых назначенных ему заданий и отключается. Целевой сервер выполняет задание локально, а затем снова подключается к главному серверу, чтобы передать результирующее состояние задания.  
  
> [!NOTE]  
> Если главный сервер недоступен в момент, когда целевой сервер пытается передать состояние задания, то сведения о состоянии задания помещаются в очередь, пока главный сервер не станет доступен.  
  
### <a name="security"></a><a name="Security"></a>безопасность  
Дополнительные сведения см. в разделах [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md) и [Choose the Right SQL Server Agent Service Account for Multiserver Environments](../../ssms/agent/choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Использование среды SQL Server Management Studio  
**Установка интервала опроса на целевых серверах**  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**, укажите пункт **Администрирование нескольких серверов**, а затем выберите пункт **Управление целевыми серверами**.  
  
3.  На вкладке **Состояние целевого сервера** выберите **Разместить инструкции**.  
  
4.  В списке **Тип инструкции** выберите **Установить интервал опроса**.  
  
5.  В диалоговом окне **Интервал опроса** введите количество секунд от 10 до 28 800, которое должно пройти до того, как целевой сервер начнет опрос главного сервера.  
  
6.  В пункте **Адресаты**выполните одно из следующих действий:  
  
    1.  Выберите пункт **Все целевые серверы** , если они имеют общий интервал опроса.  
  
    2.  Выберите пункт **Эти целевые серверы** , если не все серверы имеют общий интервал опроса, и выберите каждый целевой сервер, который будет использовать указанный интервал.  
  
## <a name="using-transact-sql"></a><a name="TSQL"></a>Использование Transact-SQL  
**Установка интервала опроса на целевых серверах**  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента Database Engine и разверните его.  
  
2.  На панели инструментов нажмите кнопку **Создать запрос**.  
  
3.  В окне запроса используйте системную хранимую процедуру [sp_post_msx_operation (Transact-SQL)](https://msdn.microsoft.com/085deef8-2709-4da9-bb97-9ab32effdacf) , чтобы задать интервал опроса для целевых серверов.  
  
## <a name="see-also"></a>См. также:  
[sysdownloadlist](../../relational-databases/system-tables/dbo-sysdownloadlist-transact-sql.md)  
  
