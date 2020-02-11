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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7189a0586ba4f62091d5eb209a56931627bc6f7f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036398"
---
# <a name="manual-commit-mode"></a>Режим ручной фиксации
*В режиме фиксации вручную* приложения должны явно завершать транзакции, вызывая **SQLEndTran** для их фиксации или отката. Это Стандартный режим транзакций для большинства реляционных баз данных.  
  
 Транзакции в ODBC не обязательно инициировать явным образом. Вместо этого транзакция запускается неявно при запуске приложения в базе данных. Если источник данных требует явной инициации транзакции, драйвер должен предоставить его всякий раз, когда приложение выполняет инструкцию, требующую транзакцию, и не имеет текущей транзакции.
