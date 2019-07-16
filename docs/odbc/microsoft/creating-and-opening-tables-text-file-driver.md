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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096546"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Создание и открытие таблиц (драйвер для текстовых файлов)
Если используется драйвер для текстовых, новая таблица создается с помощью формата, указанного в Odbcinst.ini. Если не указан, они создаются в формате CSVDELIMITED. По умолчанию 11 символов по умолчанию ЦЕЛОЧИСЛЕННЫЕ столбцы и столбцы с плавающей запятой по умолчанию 22 знаков. Столбцы ДАТ используйте формат гггг-мм-дд. CHAR и LONGCHAR столбцы являются ширины, заданной в инструкции CREATE.
