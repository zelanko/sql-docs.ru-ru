---
title: Создание и открытие таблиц (драйвер для текстовых файлов) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], creating and opening tables
ms.assetid: e6a07dda-a665-4f5b-a8d6-9ff479700513
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae13312299f131d1957557db28bbe4db0bf7b4c7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280924"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Создание и открытие таблиц (драйвер для текстовых файлов)
При использовании текстового драйвера создается новая таблица с использованием формата, указанного в Odbcinst. ini. Если не указано, таблицы создаются в формате CSVDELIMITED. По умолчанию ЦЕЛОЧИСЛЕНные столбцы по умолчанию имеют 11 символов, а столбцы с плавающей запятой по умолчанию представляют собой 22 символа. Столбцы дат используют формат гггг-мм-дд. Столбцы CHAR и ЛОНГЧАР — это ширина, указанная в инструкции CREATE.
