---
title: Вызов SQLCloseCursor | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], SQLCloseCursor
- backward compatibility [ODBC], SqlCloseCursor
- SQLCloseCursor function [ODBC], calling
- upgrading applications [ODBC], SQLCloseCursor
- compatibility [ODBC], SQLCloseCursor
ms.assetid: ef448c39-a9ad-4f07-8ef3-65bd4cef672a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 447a0892049317813fa9fe6986e6219922a11e28
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68068690"
---
# <a name="calling-sqlclosecursor"></a>Вызов SQLCloseCursor
Поскольку **SQLCloseCursor** почти так же, как **SQLFreeStmt** с SQL_CLOSE, диспетчер драйверов не сопоставляет эту функцию. Функции замены сопоставляются, так что существующие приложения ODBC *2. x* можно легко переместить в ODBC *3. x* с помощью новых функций. Такое перемещение упрощает для таких приложений использование новых функций ODBC *3. x* внутри условного кода в модульной среде. **SQLCloseCursor** не представляет никаких новых функциональных возможностей. Приложение не получает никаких преимуществ, переходя к **SQLCloseCursor** из **SQLFreeStmt** с SQL_CLOSE.
