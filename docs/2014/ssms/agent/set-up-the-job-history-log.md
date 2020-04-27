---
title: Настройка журнала заданий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 018e5c49-d3a0-4504-851a-f70996a34bb7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 613c0ccae7be912bd3bec63905b838b7f07b59b0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63033585"
---
# <a name="set-up-the-job-history-log"></a>Set Up the Job History Log
  В этом разделе описывается настройка [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журнала заданий агента.  
  
-   **Перед началом работы:**  [Безопасность](#Security)  
  
-   **Для настройки журнала заданий используется:**  [Среда SQL Server Management Studio](#SSMS)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Использование среды SQL Server Management Studio  
 **Настройка журнала заданий**  
  
1.  В **обозревателе объектов** подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Щелкните правой кнопкой мыши **агент SQL Server**, затем выберите **Свойства**.  
  
3.  В диалоговом окне **Свойства агента SQL Server** выберите страницу **Журнал** .  
  
4.  Выберите один из следующих параметров:  
  
    1.  Выберите **Ограниченный размер журнала заданий**, а затем введите максимальное число строк для журнала заданий и максимальное число строк на задание.  
  
    2.  Выберите **Автоматически удалять журнал агента**и задайте период времени, записи старше которого будут автоматически удаляться из журнала.  
  
## <a name="see-also"></a>См. также  
 [Реализация заданий](implement-jobs.md)   
 [Мониторинг активности заданий](monitor-job-activity.md)   
 [Создание заданий](create-jobs.md)  
  
  
