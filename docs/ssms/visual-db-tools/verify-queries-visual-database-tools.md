---
description: Проверка запросов (визуальные инструменты для баз данных)
title: Проверка запросов
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:100644
helpviewer_keywords:
- verifying queries
- queries [SQL Server], verifying
- checking queries
ms.assetid: 1382c0c0-46dc-45f9-ab38-9bba1d347eea
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 944d34dbbec6da87d4f3ebd7920d9acd2ad162c4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88417730"
---
# <a name="verify-queries-visual-database-tools"></a>Проверка запросов (визуальные инструменты для баз данных)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
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
  
