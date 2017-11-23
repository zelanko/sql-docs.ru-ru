---
title: "Функция SQLInstallTranslator | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLInstallTranslator
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLInstallTranslator
helpviewer_keywords: SQLInstallTranslator function [ODBC]
ms.assetid: 453b21ff-3c2b-4069-8ff7-5c727f062d89
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef9452b9ff442ec5ed40b7eb38957936d31d16b5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlinstalltranslator-function"></a>Функция SQLInstallTranslator
**Соответствия**  
 Появился в версии: ODBC 2.5, устаревшие  
  
 **Сводка**  
 В ODBC 3.0 **SQLInstallTranslator** будет заменен [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md). Вызовы **SQLInstallTranslator** будут сопоставлены с **SQLInstallTranslatorEx**. Дополнительные сведения см. в разделе **SQLInstallTranslatorEx**.  
  
 **SQLInstallTranslator** будет возвращаться значение FALSE, если приложение вызывает ее в ODBC 3*.x* диспетчера драйверов с *lpszInfFile* аргументу присвоено значение, отличное от NULL. Файл Odbc.inf, используемый в ODBC 2. *x* больше не поддерживается в ODBC 3*.x*, даже для обеспечения обратной совместимости.
