---
title: Арифметические ошибки Документы Майкрософт
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
ms.openlocfilehash: ab1b472540d1978a6e7a06d94da7542cc641e999
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299904"
---
# <a name="arithmetic-errors"></a>Ошибки арифметических действий
Драйвер ODBC оценивает положение WHERE в заявлении SELECT, поскольку он получает каждую строку. Если строка содержит значение, вызывая арифметическую ошибку, такую как разделить по нулю или числовой переполнение, драйвер возвращает все строки, но возвращает ошибки для столбцов с арифметическими ошибками. Однако при вставке или обновлении драйвер ODBC прекращает вставлять или обновлять данные при первой арифметической ошибке.
