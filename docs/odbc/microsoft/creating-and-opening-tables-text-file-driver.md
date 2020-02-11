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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b36c02d772682088a799cfca66f5bbf3e169a67f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096546"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Создание и открытие таблиц (драйвер для текстовых файлов)
При использовании текстового драйвера создается новая таблица с использованием формата, указанного в Odbcinst. ini. Если не указано, таблицы создаются в формате CSVDELIMITED. По умолчанию ЦЕЛОЧИСЛЕНные столбцы по умолчанию имеют 11 символов, а столбцы с плавающей запятой по умолчанию представляют собой 22 символа. Столбцы дат используют формат гггг-мм-дд. Столбцы CHAR и ЛОНГЧАР — это ширина, указанная в инструкции CREATE.
