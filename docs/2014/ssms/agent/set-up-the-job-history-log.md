---
title: Настройка журнала заданий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
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
ms.openlocfilehash: 0741180bb126d45ad99512a596fbab66c9a8047f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209124"
---
# <a name="set-up-the-job-history-log"></a>Set Up the Job History Log
  В этом подразделе описывается настройка журнала заданий агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Перед началом работы:**  [безопасность](#Security)  
  
-   **Для настройки журнала заданий используется:**[SQL Server Management Studio  ](#SSMS)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Использование среды SQL Server Management Studio  
 **Настройка журнала заданий**  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Щелкните правой кнопкой мыши **агент SQL Server**, затем выберите **Свойства**.  
  
3.  В диалоговом окне **Свойства агента SQL Server** выберите страницу **Журнал** .  
  
4.  Выберите из следующих параметров:  
  
    1.  Выберите **Ограниченный размер журнала заданий**, а затем введите максимальное число строк для журнала заданий и максимальное число строк на задание.  
  
    2.  Выберите **Автоматически удалять журнал агента**и задайте период времени, записи старше которого будут автоматически удаляться из журнала.  
  
## <a name="see-also"></a>См. также  
 [Реализация заданий](implement-jobs.md)   
 [Наблюдение за активностью заданий](monitor-job-activity.md)   
 [Создание заданий](create-jobs.md)  
  
  
