---
title: "Сопоставление SQLInstallTranslator | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLInstallTranslator function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLInstallTranslator
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 07308a2c737f2fbe6857d8a65a913f881b8e658f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlinstalltranslator-mapping"></a>Сопоставление SQLInstallTranslator
Когда ODBC 2. *x* приложение вызывает **SQLInstallTranslator** через ODBC 3*.x* драйвера, диспетчер драйверов сопоставляет вызов **SQLInstallTranslatorEx**. Приложение не должно вызывать **SQLInstallTranslator** в ODBC 3*.x* диспетчера драйверов с *lpszInfFile* аргументу присвоено значение, отличное от NULL. ODBC. INF-файл, используемый в ODBC 2. *x* больше не поддерживается в ODBC 3*.x*, даже для обеспечения обратной совместимости.
