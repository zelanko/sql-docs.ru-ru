---
title: Ход выполнения помощника по обновлению | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Upgrade Advisor [SQL Server], analysis progress status
- analyzing system [Upgrade Advisor], progress information
- SQL Server Upgrade Advisor, analysis progress status
- monitoring analysis progress
- progress information [Upgrade Advisor]
- status information [Upgrade Advisor]
ms.assetid: a9e3d1c8-d492-4beb-93c7-f1bc40d4a910
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e1b867360b773253ae22d24a76ce00b35c589d96
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102568"
---
# <a name="upgrade-advisor-progress"></a>Ход выполнения помощника по обновлению
  Анализ помощника по обновлению начинается с запуска выделенного анализатора, производящего анализ каждого выбранного компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Как анализа компонентов отчет о состоянии формируется в **выполняется** диалоговое окно.  
  
## <a name="options"></a>Параметры  
 **Действие**  
 Указывает выбранный для анализа компонент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Состояние**  
 Отображает значение состояния, возвращенное интерфейсом выполнения компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Сообщение**  
 Отображает сообщения об ошибке, сбое или успешном завершении, возвращенные каждым отдельным анализатором [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Если процесс анализа занял слишком много времени, можно остановить его, закрыв мастер анализа помощника по обновлению и перезапустив его. Чтобы сократить время анализа, выберите меньше компонентов для просмотра.  
  
 После завершения анализа отчет будет записан в файл. Отчет можно просмотреть, щелкнув **запустить отчет** для запуска средства просмотра отчетов на этой странице. Если вы хотите просмотреть отчет позже, можно открыть **средства просмотра отчетов помощника по обновлению** на начальной странице помощника по обновлению.  
  
> [!NOTE]  
>  Предыдущие отчеты сохраняются при каждом анализе сервера. При сохранении отчетов в качестве имени файла используется отметка времени. Средство просмотра отчетов отображает пять последних сохраненных отчетов.  
  
## <a name="see-also"></a>См. также  
 [Способ: запустите помощник по обновлению](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md)   
 [Как: запустить мастер анализа помощника по обновлению](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [Компоненты SQL Server](../../../2014/sql-server/install/sql-server-components.md)   
 [Справочник по пользовательскому интерфейсу помощника по обновлению](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)   
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  