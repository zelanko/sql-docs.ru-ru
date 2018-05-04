---
title: Сопоставление SQLInstallTranslator | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- SQLInstallTranslator function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLInstallTranslator
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00fcaf15458873da56d1d37d2234fd14bf7bbbd0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlinstalltranslator-mapping"></a>Сопоставление SQLInstallTranslator
Когда ODBC 2. *x* приложение вызывает **SQLInstallTranslator** через ODBC 3 *.x* драйвера, диспетчер драйверов сопоставляет вызов **SQLInstallTranslatorEx**. Приложение не должно вызывать **SQLInstallTranslator** в ODBC 3 *.x* диспетчера драйверов с *lpszInfFile* аргументу присвоено значение, отличное от NULL. ODBC. INF-файл, используемый в ODBC 2. *x* больше не поддерживается в ODBC 3 *.x*, даже для обеспечения обратной совместимости.
