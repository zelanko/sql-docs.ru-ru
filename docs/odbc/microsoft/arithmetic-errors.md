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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138182"
---
# <a name="arithmetic-errors"></a>Ошибки арифметических действий
Драйвер ODBC оценивает предложение WHERE в инструкции SELECT по мере выборки каждой строки. Если строка содержит значение, которое вызывает арифметическую ошибку, например деление на ноль или числовое переполнение, драйвер возвращает все строки, но возвращает ошибки для столбцов с арифметическими ошибками. Однако при вставке или обновлении драйвер ODBC прекращает вставку или обновление данных при возникновении первой арифметической ошибки.
