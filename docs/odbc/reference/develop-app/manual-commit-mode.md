---
title: "Режим ручной фиксации | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
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
ms.openlocfilehash: 666d0d7290f4878f51ad252667b3e4b778e0c501
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="manual-commit-mode"></a>Режим ручной фиксации
*В режиме ручной фиксации* приложения необходимо явно завершить транзакции путем вызова **SQLEndTran** их фиксации или отката. Это режим обычных транзакции для большинства реляционных баз данных.  
  
 Не нужно явно инициировать транзакции в ODBC. Вместо этого транзакция неявно начинается при каждом запуске приложения операционная в базе данных. Если источник данных требует запуска явной транзакции, драйвер укажите его, каждый раз, когда приложение выполняет инструкцию, требующие транзакции, и нет текущей транзакции.
