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
manager: craigg
ms.openlocfilehash: 690acf80bfabdc04d5f70b780e41943337c18cb9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792702"
---
# <a name="comparing-bookmarks"></a>Сравнение закладок
Так как закладки сравнимы байтов, их можно проверять на равенство и неравенство. Чтобы сделать это, приложение обрабатывает каждой закладке как массив байтов и сравнивает два закладки по байтам. Так как закладки, обязательно отличаться только в пределах результирующий набор, нет смысла для сравнения закладки, которые были получены из различных результирующих наборов.
