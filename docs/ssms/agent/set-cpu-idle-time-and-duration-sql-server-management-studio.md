---
description: Задание времени и длительности простоя ЦП
title: Задание времени и длительности простоя ЦП
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CPU [SQL Server], idle conditions
- time [SQL Server], CPU idle and duration
- duration of CPU idle [SQL Server]
- SQL Server Agent, CPU idle conditions
- idle time [SQL Server]
ms.assetid: 8647b465-d899-4cc7-9640-134a506d0a2e
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: 0fcfaa029005d9b45be6ce9c6e242e4e7cc0de42
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97472295"
---
# <a name="set-cpu-idle-time-and-duration"></a>Задание времени и длительности простоя ЦП

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе рассказывается о том, как задать условие простоя ЦП для сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Определение простоя ЦП влияет на то, как агент [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реагирует на события. Например, предположим, определены такие условия простоя ЦП, что средняя загрузка ЦП не превышает 10% и остается на этом уровне в течение 10 минут. Тогда, если определены задания, которые должны выполняться при достижении ЦП сервера условий простоя, выполнение задания начнется, как только загрузка ЦП упадет ниже 10% и пробудет на этом уровне 10 минут. Если это задание существенно влияет на производительность сервера, определение условий простоя ЦП имеет очень большое значение.  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-set-cpu-idle-time-and-duration"></a>Задание времени и продолжительности простоя ЦП  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Щелкните правой кнопкой мыши **Агент SQL Server**, выберите **Свойства** и перейдите на страницу **Дополнительно** .  
  
3.  В области **Условие бездействия ЦП** выполните следующие действия.  
  
    -   Установите флажок **Определите условие бездействия ЦП**.  
  
    -   Укажите процент загрузки ЦП в поле **Среднее время использования ЦП сократилось до** (для всех процессоров). Так задается максимальный уровень загрузки для времени простоя ЦП.  
  
    -   Укажите количество секунд в поле **И остается ниже этого уровня в течение** . Так задается промежуток времени, в течение которого должен сохраняться минимальный уровень загрузки ЦП, чтобы считать это простоем.  
