---
title: Окно команд
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: rothja
ms.author: jroth
ms.openlocfilehash: 1313ff25791c285e1bd1f8ccb69a75700ae62be1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063372"
---
# <a name="command-window"></a>Окно команд
  Окно **CommandWindow** используется для запуска таких команд, как команды отладки и изменения, для кода, отлаживаемого в настоящее время в окне редактора запросов компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . Чтобы иметь возможность использовать **Окно команд**, необходимо находиться в режиме отладки. Отладчик [!INCLUDE[tsql](../../includes/tsql-md.md)] поддерживает многие из команд, которые также поддерживаются средой в окне [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Команда**. Дополнительные сведения см. в разделе [Окно команд среды Visual Studio](https://go.microsoft.com/fwlink/?LinkId=112007).  
  
## <a name="task-list"></a>Список задач  
 **Доступ к окну команд**  
  
-   В меню **Отладка** выберите команду **Начать отладку**.  
  
 **Вывод значения переменной**  
  
-   В поле **CommandWindow**введите **Debug. Print \<VariableName> **, а затем нажмите клавишу ВВОД.  
  
 **Получение сведений о текущем потоке**  
  
-   В поле **CommandWindow**введите `Debug.ListThread` и нажмите клавишу ВВОД.  
  
 **Добавление переменной в окно «Быстрая проверка»**  
  
-   В поле **CommandWindow**введите **Debug. Быстрая проверка \<VariableName> **, а затем нажмите клавишу ВВОД.  
  
## <a name="see-also"></a>См. также:  
 [Отладчик Transact-SQL](transact-sql-debugger.md)  
