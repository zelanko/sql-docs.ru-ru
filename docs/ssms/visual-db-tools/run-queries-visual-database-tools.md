---
title: "Выполнение запросов (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [SQL Server], executing
- executing queries [SQL Server]
ms.assetid: 6c175c0e-55de-4bff-a53f-505c306abe25
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b2cf3c97dc3e53472fe22cefd22ee8ba0e68ca13
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="run-queries-visual-database-tools"></a>Выполнение запросов (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Завершив составление запроса, его можно выполнять.  
  
### <a name="to-execute-a-query"></a>Выполнение запроса  
  
1.  Откройте или создайте нужный запрос.  
  
2.  Щелкните любое место в окне запроса правой кнопкой мыши и в контекстном меню выберите **Выполнить SQL** .  
  
    –или–  
  
    Нажмите клавиши CTRL+R.  
  
Если запрос содержит инструкцию Select, его результаты появятся на панели результатов.  
  
Конструктор запросов и представлений возвращает результаты компьютеру в виде пакетов (последовательно), поэтому к просмотру результатов и другим задачам можно приступить сразу, не дожидаясь завершения запроса.  
  
Если запрос содержит инструкции Update, Insert From, Insert Into, Delete или Make Table, конструктор запросов и представлений отображает сообщение, показывающее, сколько строк участвовало в запросе.  
  
## <a name="see-also"></a>См. также:  
[Работа с данными на панели результатов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/work-with-data-in-the-results-pane-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
