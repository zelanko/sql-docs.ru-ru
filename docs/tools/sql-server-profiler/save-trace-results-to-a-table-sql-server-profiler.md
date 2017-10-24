---
title: "Сохранение результатов трассировки в таблицу (приложение SQL Server Profiler) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: edbecf74-683b-4e43-a1ef-7a3d5f5e27f6
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 41505214d2ae9e53cc9cd45433183d3250650313
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="save-trace-results-to-a-table-sql-server-profiler"></a>сохранять результаты трассировки в таблицу (SQL Server Profiler)
  В этом подразделе описывается, как сохранять результаты трассировок в таблицу базы данных с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-save-trace-results-to-a-table"></a>Сохранение результатов трассировки в таблицу  
  
1.  В меню **Файл** выберите пункт **Создать трассировку**, а затем подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Отображается диалоговое окно **Свойства трассировки**.  
  
    > [!NOTE]  
    >  Если установлен параметр **Начать трассировку немедленно после установления соединения**, диалоговое окно **Свойства трассировки**не отображается, а вместо этого начинается трассировка. Чтобы отключить этот параметр, в меню **Сервис**выберите пункт **Параметры**и снимите флажок **Начать трассировку немедленно после установления соединения** .  
  
2.  В поле **Имя трассировки** введите имя трассировки и нажмите кнопку **Сохранить в таблицу**.  
  
3.  В диалоговом окне **Соединение с сервером** подключитесь к содержащей таблицу трассировок базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
4.  В диалоговом окне **Целевая таблица** выберите базу данных из списка **База данных**.  
  
5.  В списке **Владелец** выберите владельца трассировки.  
  
6.  В списке **Таблица** введите или выберите имя таблицы для сохранения результатов трассировки. Нажмите кнопку **ОК.**  
  
7.  В диалоговом окне **Свойства трассировки** установите флажок **Максимальное число строк (тыс.)**, чтобы задать максимальное число строк для сохранения.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  

