---
title: "Изменение размера журнала заданий | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], history
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 82aede2ce0a0f0a0271e73361292628049f97875
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="resize-the-job-history-log"></a>Изменение размера журнала заданий
В этом разделе описывается задание ограничений на размер журналов заданий агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в среде [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
-   **Перед началом работы выполните следующие действия.**  
  
    [безопасность](#Security)  
  
-   **Для задания ограничений на размер журнала заданий используется:**  
  
    [Среда Среда SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-resize-the-job-history-log-based-on-raw-size"></a>Изменение размера журнала заданий, основанного на необработанном размере  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Щелкните правой кнопкой мыши **агент SQL Server**, затем выберите **Свойства**.  
  
3.  Выберите страницу **Журнал** и убедитесь, что флажок **Ограниченный размер журнала заданий**установлен.  
  
4.  В диалоговом окне **Максимальный размер журнала заданий** введите максимальное число строк для журнала заданий.  
  
5.  В диалоговом окне **Максимальное число строк журнала для одного задания** введите максимальное число строк журнала для одного задания.  
  
#### <a name="to-resize-the-job-history-log-based-on-time"></a>Изменить размера журнала заданий, основанного на времени  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Щелкните правой кнопкой мыши **агент SQL Server**, затем выберите **Свойства**.  
  
3.  Выберите страницу **Журнал** и щелкните **Автоматически удалять журнал агента**.  
  
4.  Выберите подходящее количество **дней**, **недель**или **месяцев**.  
  

