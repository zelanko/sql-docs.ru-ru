---
title: Сравнение закладок | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 44da652ad1e52934fa48f32b1b2f88b30212ad3b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083308"
---
# <a name="comparing-bookmarks"></a>Сравнение закладок
Так как закладки сравнимы байтов, их можно проверять на равенство и неравенство. Чтобы сделать это, приложение обрабатывает каждой закладке как массив байтов и сравнивает два закладки по байтам. Так как закладки, обязательно отличаться только в пределах результирующий набор, нет смысла для сравнения закладки, которые были получены из различных результирующих наборов.
