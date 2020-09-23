---
description: Resize the Job History Log
title: Resize the Job History Log
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
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 99a06d15025dd4a8ee6970aeb5175bbe58d4cc36
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492070"
---
# <a name="resize-the-job-history-log"></a>Resize the Job History Log

[!INCLUDE[applies-to-version/_ssnoversion.md](../../includes/applies-to-version/sqlserver.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этой статье описывается, как установить ограничения на размер журналов заданий агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].

- **Перед началом работы**  

    [Безопасность](#Security)  

- **Для задания ограничений на размер журнала заданий используется:**  

    [Среда SQL Server Management Studio](#SSMS)

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Перед началом  

### <a name="security"></a><a name="Security"></a>безопасность

Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md).  

## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Использование среды SQL Server Management Studio

*Изменение размера журнала заданий, основанного на необработанном размере*

1. В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.

2. Щелкните правой кнопкой мыши элемент **Агент SQL Server** и выберите пункт **Свойства**.

3. Выберите страницу **Журнал** и убедитесь, что флажок **Ограниченный размер журнала заданий** установлен.

4. В диалоговом окне **Максимальный размер журнала заданий** введите максимальное число строк для журнала заданий.

5. В диалоговом окне **Максимальное число строк журнала для одного задания** введите максимальное число строк журнала для одного задания.

**Изменение размера журнала заданий, основанного на времени**

1. В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  

2. Щелкните правой кнопкой мыши элемент **Агент SQL Server** и выберите пункт **Свойства**.

3. Выберите страницу **Журнал**, а затем выберите **Удалять журнал агента**.

4. Выберите подходящее количество **дней**, **недель** или **месяцев**.
