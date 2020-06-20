---
title: Ход выполнения советника по переходу | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], analysis progress status
- analyzing system [Upgrade Advisor], progress information
- SQL Server Upgrade Advisor, analysis progress status
- monitoring analysis progress
- progress information [Upgrade Advisor]
- status information [Upgrade Advisor]
ms.assetid: a9e3d1c8-d492-4beb-93c7-f1bc40d4a910
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 692b06051872084ff5e1b16dfaf1f8198a649d62
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062336"
---
# <a name="upgrade-advisor-progress"></a>Ход выполнения помощника по обновлению
  Анализ помощника по обновлению начинается с запуска выделенного анализатора, производящего анализ каждого выбранного компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По мере анализа компонентов в диалоговом окне **ход** выполнения отображается ход выполнения.  
  
## <a name="options"></a>Варианты  
 **Действие**  
 Указывает выбранный для анализа компонент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Состояние**  
 Отображает значение состояния, возвращенное интерфейсом выполнения компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Message**  
 Отображает сообщения об ошибке, сбое или успешном завершении, возвращенные каждым отдельным анализатором [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Если процесс анализа занял слишком много времени, можно остановить его, закрыв мастер анализа помощника по обновлению и перезапустив его. Чтобы сократить время анализа, выберите меньше компонентов для просмотра.  
  
 После завершения анализа отчет будет записан в файл. Чтобы просмотреть отчет, нажмите кнопку **запустить отчет** , чтобы запустить средство просмотра отчетов с этой страницы. Если вы хотите просмотреть отчет позже, можно открыть **средство просмотра отчетов помощника по обновлению** на начальной странице помощника по обновлению.  
  
> [!NOTE]  
>  Предыдущие отчеты сохраняются при каждом анализе сервера. При сохранении отчетов в качестве имени файла используется отметка времени. Средство просмотра отчетов отображает пять последних сохраненных отчетов.  
  
## <a name="see-also"></a>См. также:  
 [Руководство. Запуск помощника по обновлению](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md)   
 [Как запустить мастер анализа помощника по обновлению](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [Компоненты SQL Server](../../../2014/sql-server/install/sql-server-components.md)   
 [Справочник по пользовательскому интерфейсу помощника по обновлению](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)   
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
