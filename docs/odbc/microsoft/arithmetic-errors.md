---
title: Арифметические ошибки | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e52d0edb1704df3e4085e417493fd68b7a7af977
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="arithmetic-errors"></a>Арифметические ошибки
Драйвер ODBC вычисляет предложения WHERE в инструкции SELECT, он извлекает каждую строку. Если строка содержит значение, которое вызывает арифметическую ошибку переполнения, деления на ноль или numeric, например, драйвер возвращает все строки, но возвращает ошибки для столбцов с помощью арифметических ошибок. При вставке или обновлении, однако драйвер ODBC останавливается, вставка или обновление данных при обнаружении первой ошибки арифметического.
