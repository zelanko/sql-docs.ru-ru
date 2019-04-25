---
title: Режим ручной фиксации | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- manual-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1952d4185c80a3b49b7742a9dba1f3d8d41a6ca6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62628919"
---
# <a name="manual-commit-mode"></a>Режим ручной фиксации
*В режиме ручной фиксации* приложения необходимо явно завершить транзакции путем вызова **SQLEndTran** их фиксации или отката. Этот режим используется по обычной транзакций для большинства реляционных баз данных.  
  
 Транзакции в ODBC, нет необходимости явно инициировать. Вместо этого транзакция неявно начинается при каждом запуске приложения, работающие с базы данных. Если источник данных требует запуска явной транзакции, драйвер должен указать каждый раз, когда приложение выполняет инструкцию, требующие транзакции, и нет текущей транзакции.
