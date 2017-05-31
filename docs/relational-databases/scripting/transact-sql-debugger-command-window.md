---
title: "Командное окно | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 328c018f1b1b62ce578f849e88301d554142ee00
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="transact-sql-debugger---command-window"></a>Отладчик Transact-SQL, командное окно
  Окно **CommandWindow** используется для запуска таких команд, как команды отладки и изменения, для кода, отлаживаемого в настоящее время в окне редактора запросов компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . Чтобы иметь возможность использовать **Окно команд**, необходимо находиться в режиме отладки. Отладчик [!INCLUDE[tsql](../../includes/tsql-md.md)] поддерживает многие из команд, которые также поддерживаются средой [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Окно** . Дополнительные сведения см. в разделе [Окно команд среды Visual Studio](http://go.microsoft.com/fwlink/?LinkId=112007).  
  
## <a name="task-list"></a>Список задач  
 **Доступ к окну команд**  
  
-   В меню **Отладка** выберите команду **Начать отладку**.  
  
 **Вывод значения переменной**  
  
-   В окне **CommandWindow** введите **Debug.Print \<имя_переменной>** и нажмите клавишу ВВОД.  
  
 **Получение сведений о текущем потоке**  
  
-   В окне **CommandWindow**введите **Debug.ListThread**и нажмите клавишу ВВОД.  
  
 **Добавление переменной в окно «Быстрая проверка»**  
  
-   В окне **CommandWindow** введите **Debug.QuickWatch \<имя_переменной>** и нажмите клавишу ВВОД.  
  
## <a name="see-also"></a>См. также:  
 [Отладчик Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)  
  
  
