---
title: Создание и открытие таблицы (Драйвер текстовых файлов) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280924"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Создание и открытие таблиц (драйвер для текстовых файлов)
При использовании драйвера текста создается новая таблица с использованием формата, указанного в Odbcinst.ini. Если не указано, таблицы создаются в формате CSVDELIMITED. По умолчанию, INTEGER столбцов по умолчанию 11 символов и FLOAT столбцов по умолчанию до 22 символов. В столбцах DATE используется формат YYYY-MM-DD. Столбцы CHAR и LONGCHAR являются шириной, указанной в заявлении CREATE.
