---
title: Изменение размера журнала заданий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f1a8c9ab517d1f6a122144604d6b147e6f5eeaf6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62650891"
---
# <a name="resize-the-job-history-log"></a>Изменение размера журнала заданий
  В этом разделе описывается задание ограничений на размер журналов заданий агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в среде [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   **Перед началом:**  
  
     [безопасность](#Security)  
  
-   **Для задания ограничений на размер журнала заданий используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-resize-the-job-history-log-based-on-raw-size"></a>Изменение размера журнала заданий, основанного на необработанном размере  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Щелкните правой кнопкой мыши **агент SQL Server**, затем выберите **Свойства**.  
  
3.  Выберите страницу **Журнал** и убедитесь, что флажок **Ограниченный размер журнала заданий**установлен.  
  
4.  В диалоговом окне **Максимальный размер журнала заданий** введите максимальное число строк для журнала заданий.  
  
5.  В диалоговом окне **Максимальное число строк журнала для одного задания** введите максимальное число строк журнала для одного задания.  
  
#### <a name="to-resize-the-job-history-log-based-on-time"></a>Изменить размера журнала заданий, основанного на времени  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Щелкните правой кнопкой мыши **агент SQL Server**, затем выберите **Свойства**.  
  
3.  Выберите страницу **Журнал** и щелкните **Автоматически удалять журнал агента**.  
  
4.  Выберите подходящее количество **дней**, **недель**или **месяцев**.  
  
  
