---
title: Параметры (результаты SQL Server-Multi сервер запросов) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.sqleditors.multiserverresultssettings
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLMultiServerResults
ms.assetid: d6768bd8-9cb5-4606-a726-a33a1df9e1bb
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a1465defc783d0fde352a29648af61c0bb99ff59
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098251"
---
# <a name="options-query-results-sql-server-multi-server"></a>Параметры (результаты SQL Server-Multi сервер запросов)
  При одновременном выполнении запросов для нескольких серверов с помощью этой страницы можно указать параметры отображения результирующих наборов. Слияние результатов объединяет результирующие наборы всех серверов в единый результирующий набор. При объединении результатов первый ответивший сервер устанавливает схему результирующего набора. Для объединения результирующих наборов запрос должен вернуть одинаковое число столбцов с одинаковыми для каждого сервера именами. При слиянии результатов будет выведено сообщение для каждого сервера, результаты которого не совпадают со схемой (количество и имена столбцов), возвращенной первым сервером, возвратившим результаты.  
  
 Если слияние результатов не выполняется, результирующий набор каждого сервера будет отображен в своей собственной сетке со своей собственной схемой.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Произвести слияние результатов**  
 Установите данный флажок, чтобы объединить результирующие наборы нескольких серверов в одну сетку.  
  
 **Добавить к результатам имя сервера**  
 Установите данный флажок, чтобы включить дополнительный столбец, в котором указывается имя сервера, вернувшего каждую из строк.  
  
 **Добавить имя входа к результатам**  
 Установите данный флажок, чтобы включить дополнительный столбец, в котором указывается имя входа, использованное для подключения к серверу, предоставившему каждую из строк.  
  
## <a name="see-also"></a>См. также  
 [Создание сервера централизованного управления и группы серверов &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)   
 [Выполнение инструкции на нескольких серверах одновременно (среда SQL Server Management Studio)](../ssms/register-servers/execute-statements-against-multiple-servers-simultaneously.md)  
  
  