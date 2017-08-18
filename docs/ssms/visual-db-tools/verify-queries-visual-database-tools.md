---
title: "Проверка запросов (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdtsql.chm:100644
helpviewer_keywords:
- verifying queries
- queries [SQL Server], verifying
- checking queries
ms.assetid: 1382c0c0-46dc-45f9-ab38-9bba1d347eea
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e2aa0172a18bb1b01297caa9dcf4db07888ce083
ms.contentlocale: ru-ru
ms.lasthandoff: 08/18/2017

---
# <a name="verify-queries-visual-database-tools"></a>Проверка запросов (визуальные инструменты для баз данных)
Чтобы избежать проблем, можно проверить созданный запрос, чтобы гарантировать правильность его синтаксиса. Эта возможность особенно полезна при вводе инструкций на [панели SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
Некоторые особенности, которые нужно иметь в виду при проверке запросов:  
  
-   Инструкция может быть правильной, и поэтому успешно проверяться, даже если она не может быть представлена на **панели диаграммы** и **панели критериев**.  
  
-   Проверка SQL может обнаружить некоторые, но не все ошибки языка SQL. Если запрос будет содержать ошибку, не обнаруженную в ходе проверки синтаксиса SQL, то база данных обнаружит ошибку при выполнении запроса.  
  
-   Запросы, содержащие параметры, не могут быть проверены.  
  
### <a name="to-verify-an-sql-statement"></a>Проверка инструкции SQL  
  
-   Щелкните правой кнопкой мыши любое место на **панели SQL**и выберите из контекстного меню пункт **Проверить синтаксис SQL** .  
  
## <a name="see-also"></a>См. также:  
[Выполнение запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/run-queries-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  

