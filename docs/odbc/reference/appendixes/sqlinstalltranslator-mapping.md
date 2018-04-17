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
ms.topic: article
helpviewer_keywords:
- SQLInstallTranslator function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLInstallTranslator
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 559cbd719ae25a607cc7336df085799369b048df
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlinstalltranslator-mapping"></a>Сопоставление SQLInstallTranslator
Когда ODBC 2. *x* приложение вызывает **SQLInstallTranslator** через ODBC 3*.x* драйвера, диспетчер драйверов сопоставляет вызов **SQLInstallTranslatorEx**. Приложение не должно вызывать **SQLInstallTranslator** в ODBC 3*.x* диспетчера драйверов с *lpszInfFile* аргументу присвоено значение, отличное от NULL. ODBC. INF-файл, используемый в ODBC 2. *x* больше не поддерживается в ODBC 3*.x*, даже для обеспечения обратной совместимости.
