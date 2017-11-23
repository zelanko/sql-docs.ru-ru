---
title: "Режим ручной фиксации | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rolling back transactions [ODBC]
- manual-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b3838b390c41dfab8010d728e1eab8bb5f410c67
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="manual-commit-mode"></a>Режим ручной фиксации
*В режиме ручной фиксации* приложения необходимо явно завершить транзакции путем вызова **SQLEndTran** их фиксации или отката. Это режим обычных транзакции для большинства реляционных баз данных.  
  
 Не нужно явно инициировать транзакции в ODBC. Вместо этого транзакция неявно начинается при каждом запуске приложения операционная в базе данных. Если источник данных требует запуска явной транзакции, драйвер укажите его, каждый раз, когда приложение выполняет инструкцию, требующие транзакции, и нет текущей транзакции.
