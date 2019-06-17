---
title: Арифметические ошибки | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0d957d6091dc5fa29ee8a0b707c0e7fe7dfc7c8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63302039"
---
# <a name="arithmetic-errors"></a>Ошибки арифметических действий
Драйвер ODBC оценивает предложение WHERE в инструкции SELECT, так как она получает каждой строки. Если строка содержит значение, которое вызывает арифметическую ошибку, например переполнение, деление на ноль или числовое, драйвер возвращает все строки, но возвращает ошибки для столбцов с помощью арифметических ошибок. При вставке или обновлении, тем не менее, драйвер ODBC останавливает, вставки или обновления данных при обнаружении первой арифметические ошибки.
