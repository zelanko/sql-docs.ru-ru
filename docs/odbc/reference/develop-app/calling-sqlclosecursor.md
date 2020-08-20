---
description: Вызов SQLCloseCursor
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
ms.openlocfilehash: 925617d79266f0b50ef9b38586b31af91311b63e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494774"
---
# <a name="calling-sqlclosecursor"></a>Вызов SQLCloseCursor
Поскольку **SQLCloseCursor** почти так же, как **SQLFreeStmt** с SQL_CLOSE, диспетчер драйверов не сопоставляет эту функцию. Функции замены сопоставляются, так что существующие приложения ODBC *2. x* можно легко переместить в ODBC *3. x* с помощью новых функций. Такое перемещение упрощает для таких приложений использование новых функций ODBC *3. x* внутри условного кода в модульной среде. **SQLCloseCursor** не представляет никаких новых функциональных возможностей. Приложение не получает никаких преимуществ, переходя к **SQLCloseCursor** из **SQLFreeStmt** с SQL_CLOSE.
