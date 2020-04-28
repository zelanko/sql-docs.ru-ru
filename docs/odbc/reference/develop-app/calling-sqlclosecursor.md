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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2feab58de28e39747a1d9c819f9f15426b156151
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306277"
---
# <a name="calling-sqlclosecursor"></a>Вызов SQLCloseCursor
Поскольку **SQLCloseCursor** почти так же, как **SQLFreeStmt** с SQL_CLOSE, диспетчер драйверов не сопоставляет эту функцию. Функции замены сопоставляются, так что существующие приложения ODBC *2. x* можно легко переместить в ODBC *3. x* с помощью новых функций. Такое перемещение упрощает для таких приложений использование новых функций ODBC *3. x* внутри условного кода в модульной среде. **SQLCloseCursor** не представляет никаких новых функциональных возможностей. Приложение не получает никаких преимуществ, переходя к **SQLCloseCursor** из **SQLFreeStmt** с SQL_CLOSE.
