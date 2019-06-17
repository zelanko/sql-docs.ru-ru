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
manager: craigg
ms.openlocfilehash: ce901e6a8639c8a2caea6e55cbaa18fedb56f4a7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63132731"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Создание и открытие таблиц (драйвер для текстовых файлов)
Если используется драйвер для текстовых, новая таблица создается с помощью формата, указанного в Odbcinst.ini. Если не указан, они создаются в формате CSVDELIMITED. По умолчанию 11 символов по умолчанию ЦЕЛОЧИСЛЕННЫЕ столбцы и столбцы с плавающей запятой по умолчанию 22 знаков. Столбцы ДАТ используйте формат гггг-мм-дд. CHAR и LONGCHAR столбцы являются ширины, заданной в инструкции CREATE.
