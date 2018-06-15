---
title: Сравнение закладки | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1cb844592d47e46a38f431f0127845583b82498a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909379"
---
# <a name="comparing-bookmarks"></a>Сравнение закладки
Поскольку закладки сравнимы байтов, их можно проверять на равенство и неравенство. Чтобы сделать это, приложение обрабатывает каждой закладке как массив байтов и сравнивает две закладки байт за байтом. Поскольку закладки, обязательно отличаться только внутри результирующего набора, нет смысла для сравнения закладки, которые были получены из различных результирующих наборов.
