---
title: Скрипт отладки | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Script task [Integration Services], debugging
- debugging [Integration Services], scripts
- scripts [Integration Services], debugging
ms.assetid: fddf57d8-8607-4f88-85a0-1b683087b491
caps.latest.revision: 56
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 55e6df8e55d0805f6ac33accc427ed7734d4eb97
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096196"
---
# <a name="debugging-script"></a>Скрипт отладки
  Скрипты, использующие задачу и компонент "Скрипт", создаются в средствах для приложений [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (VSTA).  
  
 Можно задавать и использовать в скриптах точки останова в VSTA. VSTA дает возможность управлять точками останова, но для этого вы можете также пользоваться и диалоговым окном **Задание точек останова** конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Дополнительные сведения см. в статье [Debugging Control Flow](debugging-control-flow.md).  
  
 Диалоговое окно **Задание точек останова** включает точки останова скрипта. Они содержатся внизу списка точек останова и отображают номер строки и имя функции, в которой появляется точка останова. Точки останова скрипта вы можете удалять с помощью диалогового окна **Задание точек останова** .  
  
 Во время выполнения точки останова, заданные для строк кода скрипта, объединяются с точками останова, заданными для пакета или задач и контейнеров в пакете. Отладчик может выполняться от точки останова в скрипте до точки останова, заданной для пакета задачи или контейнера, и наоборот. Например, для пакета могут существовать точки останова, заданные условиями останова, возникающими при получении пакетом событий **OnPreExecute** и **OnPostExecute** , а также задача «Скрипт» с точками останова для строк скрипта. В этом случае пакет может приостановить выполнение по условию останова, связанного с событием **OnPreExecute** , выполниться до точки останова в скрипте и в заключение до условия останова, связанного с событием **OnPostExecute** .  
  
 Дополнительные сведения об отладке задачи и компонента «Скрипт» см. в разделах [Coding and Debugging the Script Task](../extending-packages-scripting/task/coding-and-debugging-the-script-task.md) и [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="to-set-a-breakpoint-in-visual-studio-for-applications"></a>Задание точки останова в Visual Studio для приложений  
  
-   [Отладка скрипта с помощью точек останова в задаче и компоненте «Скрипт»](../extending-packages-scripting/debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component.md)  
  
## <a name="see-also"></a>См. также  
 [Инструменты устранения неполадок при разработке пакета](troubleshooting-tools-for-package-development.md)  
  
  