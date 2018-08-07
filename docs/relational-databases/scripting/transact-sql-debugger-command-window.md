---
title: Командное окно | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 5f406e86e4a32d8d096b5082ca2dfa733013cdc2
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39539984"
---
# <a name="transact-sql-debugger---command-window"></a>Отладчик Transact-SQL, командное окно
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
  
  
