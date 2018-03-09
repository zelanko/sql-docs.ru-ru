---
title: "Арифметические ошибки | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a0a24a87c814c51bcf3270298b56b5ffec01fa29
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="arithmetic-errors"></a>Арифметические ошибки
Драйвер ODBC вычисляет предложения WHERE в инструкции SELECT, он извлекает каждую строку. Если строка содержит значение, которое вызывает арифметическую ошибку переполнения, деления на ноль или numeric, например, драйвер возвращает все строки, но возвращает ошибки для столбцов с помощью арифметических ошибок. При вставке или обновлении, однако драйвер ODBC останавливается, вставка или обновление данных при обнаружении первой ошибки арифметического.
