---
title: Режим фиксации вручную | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2a00ff373e374d0940b3e7259eeb01e26b620cae
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81287878"
---
# <a name="manual-commit-mode"></a>Режим ручной фиксации
*В режиме фиксации вручную* приложения должны явно завершать транзакции, вызывая **SQLEndTran** для их фиксации или отката. Это Стандартный режим транзакций для большинства реляционных баз данных.  
  
 Транзакции в ODBC не обязательно инициировать явным образом. Вместо этого транзакция запускается неявно при запуске приложения в базе данных. Если источник данных требует явной инициации транзакции, драйвер должен предоставить его всякий раз, когда приложение выполняет инструкцию, требующую транзакцию, и не имеет текущей транзакции.
