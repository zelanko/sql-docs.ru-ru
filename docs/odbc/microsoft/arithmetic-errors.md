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
ms.openlocfilehash: 2e0880e1746b4b65070fb28bf8d83aadec301aa4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138182"
---
# <a name="arithmetic-errors"></a>Ошибки арифметических действий
Драйвер ODBC оценивает предложение WHERE в инструкции SELECT, так как она получает каждой строки. Если строка содержит значение, которое вызывает арифметическую ошибку, например переполнение, деление на ноль или числовое, драйвер возвращает все строки, но возвращает ошибки для столбцов с помощью арифметических ошибок. При вставке или обновлении, тем не менее, драйвер ODBC останавливает, вставки или обновления данных при обнаружении первой арифметические ошибки.
