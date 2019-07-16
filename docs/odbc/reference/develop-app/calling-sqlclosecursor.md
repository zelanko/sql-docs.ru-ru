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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68068690"
---
# <a name="calling-sqlclosecursor"></a>Вызов SQLCloseCursor
Так как **SQLCloseCursor** практически не отличается от как **SQLFreeStmt** с SQL_CLOSE, диспетчер драйверов не соответствует этой функции. Функции замены сопоставляются таким образом, чтобы существующие ODBC *2.x* приложений можно легко переместить в ODBC *3.x* с помощью новых функций. Это решение упрощает для таких приложений начать работу с новой ODBC *3.x* функции внутри условного кода в модульном варианте. **SQLCloseCursor** не представляет никаких новых функциональных возможностей. Приложения не смогут получить все преимущества, переместив **SQLCloseCursor** из **SQLFreeStmt** с SQL_CLOSE.
