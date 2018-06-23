---
title: Проверка запросов (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vdtsql.chm:100644
helpviewer_keywords:
- verifying queries
- queries [SQL Server], verifying
- checking queries
ms.assetid: 1382c0c0-46dc-45f9-ab38-9bba1d347eea
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6f77da9093a27456014f78ca6285a33d3c565bf2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087042"
---
# <a name="verify-queries-visual-database-tools"></a>Проверка запросов (визуальные инструменты для баз данных)
  Чтобы избежать проблем, можно проверить созданный запрос, чтобы гарантировать правильность его синтаксиса. Эта возможность особенно полезна при вводе инструкций на [панели SQL](visual-database-tools.md).  
  
 Некоторые особенности, которые нужно иметь в виду при проверке запросов:  
  
-   Инструкция может быть правильной, и поэтому успешно проверяться, даже если она не может быть представлена на **панели диаграммы** и **панели критериев**.  
  
-   Проверка SQL может обнаружить некоторые, но не все ошибки языка SQL. Если запрос будет содержать ошибку, не обнаруженную в ходе проверки синтаксиса SQL, то база данных обнаружит ошибку при выполнении запроса.  
  
-   Запросы, содержащие параметры, не могут быть проверены.  
  
### <a name="to-verify-an-sql-statement"></a>Проверка инструкции SQL  
  
-   Щелкните правой кнопкой мыши любое место на **панели SQL**и выберите из контекстного меню пункт **Проверить синтаксис SQL** .  
  
## <a name="see-also"></a>См. также  
 [Выполнение запросов &#40;визуальные средства базы данных&#41;](run-queries-visual-database-tools.md)   
 [Выполнение основных операций с запросами (визуальные инструменты для баз данных)](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  