---
description: Создание и открытие таблиц (драйвер для текстовых файлов)
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
ms.openlocfilehash: c64f74270e8c2bbf4645f72406113e88948d0da9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340970"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Создание и открытие таблиц (драйвер для текстовых файлов)
При использовании текстового драйвера создается новая таблица с использованием формата, указанного в Odbcinst.ini. Если не указано, таблицы создаются в формате CSVDELIMITED. По умолчанию ЦЕЛОЧИСЛЕНные столбцы по умолчанию имеют 11 символов, а столбцы с плавающей запятой по умолчанию представляют собой 22 символа. Столбцы дат используют формат гггг-мм-дд. Столбцы CHAR и ЛОНГЧАР — это ширина, указанная в инструкции CREATE.
