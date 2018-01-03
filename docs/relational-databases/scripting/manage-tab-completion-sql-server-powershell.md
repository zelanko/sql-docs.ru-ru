---
title: "Управление завершением по нажатию клавиши Tab (SQL Server PowerShell) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6296848a-890f-4ad3-8d9f-92ed6a79aa00
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 012deb0010431ee9bc50a3a470c3e3a00a15d19e
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="manage-tab-completion-sql-server-powershell"></a>Управление завершением по нажатию клавиши Tab (SQL Server PowerShell)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Оснастки PowerShell [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляют три переменные для управления завершением Windows PowerShell по нажатию клавиши TAB: **$SqlServerMaximumTabCompletion**, **$SqlServerMaximumChildItems** и **$SqlServerIncludeSystemObjects**. Функция завершения по клавише TAB позволяет сократить объем вводимого текста, поскольку возвращает таблицы элементов, имена которых начинаются с набранной строки.  
  
## <a name="before-you-begin"></a>Перед началом  
 Функция завершения по клавише TAB среды Windows PowerShell дает возможность после ввода части имени пути или командлета нажать клавишу TAB, чтобы получить список элементов, имена которых согласуются с уже набранным текстом. Затем можно выбрать нужный элемент из списка, не набирая остальную часть его имени.  
  
 При работе с базой данных, содержащей большое количество объектов, списки завершения по клавише TAB могут стать очень большими. Кроме того, для некоторых типов объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , например представлений, предусмотрено большое число системных объектов.  
  
 В оснастках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] впервые представлены три системные переменные, которые позволяют управлять объемом данных, выводимых функцией завершения по клавише TAB и командлетом **Get-ChildItem**.  
  
 **$SqlServerMaximumTabCompletion =** *n*  
 Указывает максимальное число объектов, включаемых в список завершения по клавише TAB. Если нажать клавишу TAB в узле пути, для которого существует более *n* подходящих объектов, выводимый список завершения будет усечен до *n*. *n* имеет тип integer. 0 — значение по умолчанию, которое означает, что число перечисляемых объектов не ограничено.  
  
 **$SqlServerMaximumChildItems =** *n*  
 Указывает максимальное количество объектов, отображаемых командлетом **Get-ChildItem**. Если командлет **Get-ChildItem** выполняется в узле пути, для которого существует более *n* объектов, список будет усечен до *n*. *n* имеет тип integer. 0 — значение по умолчанию, которое означает, что число перечисляемых объектов не ограничено.  
  
 **$SqlServerIncludeSystemObjects =** { **$True** | **$False** }  
 Если указано значение **$True**, функция завершения по клавише TAB и командлет **Get-ChildItem**отображают системные объекты. Если значение равно **$False**, системные объекты не отображаются. Значение по умолчанию — **$False**.  
  
## <a name="set-the-sql-server-tab-completion-variables"></a>Установка переменных функции завершения по клавише TAB для SQL Server  
 Задайте новое значение для любой переменной, значение которой необходимо заменить на отличное от применяемого по умолчанию.  
  
### <a name="example-powershell"></a>Пример (PowerShell)  
 В следующем примере задаются все три переменные и выводятся их значения:  
  
```  
$SqlServerMaximumTabCompletion = 20  
$SqlServerMaximumChildItems = 10  
$SqlServerIncludeSystemObjects = $False  
dir variable:sqlserver*  
```  
  
## <a name="see-also"></a>См. также:  
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  
