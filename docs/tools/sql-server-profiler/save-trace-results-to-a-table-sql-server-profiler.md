---
title: "Сохранение результатов трассировки в таблицу (приложение SQL Server Profiler) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: edbecf74-683b-4e43-a1ef-7a3d5f5e27f6
caps.latest.revision: "24"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f411639ced17e80acca493e7e0cd23de6ed5bc8c
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="save-trace-results-to-a-table-sql-server-profiler"></a>сохранять результаты трассировки в таблицу (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]В этом разделе описывается сохранение результатов трассировки в таблицу базы данных с помощью [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
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
  
  
