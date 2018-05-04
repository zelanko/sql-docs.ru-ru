---
title: Режим ручной фиксации | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- manual-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bdf722c77071a3958f115e573bfe227f9561dd01
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="manual-commit-mode"></a>Режим ручной фиксации
*В режиме ручной фиксации* приложения необходимо явно завершить транзакции путем вызова **SQLEndTran** их фиксации или отката. Это режим обычных транзакции для большинства реляционных баз данных.  
  
 Не нужно явно инициировать транзакции в ODBC. Вместо этого транзакция неявно начинается при каждом запуске приложения операционная в базе данных. Если источник данных требует запуска явной транзакции, драйвер укажите его, каждый раз, когда приложение выполняет инструкцию, требующие транзакции, и нет текущей транзакции.
