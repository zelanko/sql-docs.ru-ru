---
title: Проверка запросов (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: 3848b8cc758dde890c06711b4bea4e70cd137bb2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33048461"
---
# <a name="verify-queries-visual-database-tools"></a>Проверка запросов (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
  
