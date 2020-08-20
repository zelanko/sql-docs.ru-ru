---
description: Ошибки арифметических действий
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e2fa142b43f1e96693390f777c90ea6f10705f6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500407"
---
# <a name="arithmetic-errors"></a>Ошибки арифметических действий
Драйвер ODBC оценивает предложение WHERE в инструкции SELECT по мере выборки каждой строки. Если строка содержит значение, которое вызывает арифметическую ошибку, например деление на ноль или числовое переполнение, драйвер возвращает все строки, но возвращает ошибки для столбцов с арифметическими ошибками. Однако при вставке или обновлении драйвер ODBC прекращает вставку или обновление данных при возникновении первой арифметической ошибки.
