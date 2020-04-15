---
title: Режим ручного обязательства (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287878"
---
# <a name="manual-commit-mode"></a>Режим ручной фиксации
*В режиме ручного коммита* приложения должны явно выполнять транзакции, вызывая **S'LEndTran,** чтобы выполнить их или откатить. Это обычный режим транзакций для большинства реляционных баз данных.  
  
 Сделки в ODBC не должны быть явно инициированы. Вместо этого транзакция начинается неявно всякий раз, когда приложение начинает работать в базе данных. Если источник данных требует явного инициирования транзакции, драйвер должен предоставить его всякий раз, когда приложение выполняет заявление, требующее транзакции, и нет текущей транзакции.
