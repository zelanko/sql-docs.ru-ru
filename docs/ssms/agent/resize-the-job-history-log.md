---
title: Resize the Job History Log
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 45f53291d70d08fa75ab158db3911c058fdba5c7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75253526"
---
# <a name="resize-the-job-history-log"></a>Resize the Job History Log
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md.md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этой статье описывается, как установить ограничения на размер журналов заданий агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
  
-   **Перед началом работы**  
  
    [Безопасность](#Security)  
  
-   **Для задания ограничений на размер журнала заданий используется:**  
  
    [Среда SQL Server Management Studio](#SSMS)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="security"></a><a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
*Изменение размера журнала заданий, основанного на необработанном размере*
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Щелкните правой кнопкой мыши **агент SQL Server**, затем выберите **Свойства**.  
  
3.  Выберите страницу **Журнал** и убедитесь, что флажок **Ограниченный размер журнала заданий** установлен.  
  
4.  В диалоговом окне **Максимальный размер журнала заданий** введите максимальное число строк для журнала заданий.  
  
5.  В диалоговом окне **Максимальное число строк журнала для одного задания** введите максимальное число строк журнала для одного задания.  
  
**Изменение размера журнала заданий, основанного на времени**
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Щелкните правой кнопкой мыши **агент SQL Server**, затем выберите **Свойства**.  
  
3.  Выберите страницу **Журнал** и щелкните **Автоматически удалять журнал агента**.  
  
4.  Выберите подходящее количество **дней**, **недель** или **месяцев**.  
  
