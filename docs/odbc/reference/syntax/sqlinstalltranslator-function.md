---
title: Функция SQLInstallTranslator | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLInstallTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallTranslator
helpviewer_keywords:
- SQLInstallTranslator function [ODBC]
ms.assetid: 453b21ff-3c2b-4069-8ff7-5c727f062d89
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 92ae84714ad78e6dca3a653b85b7815188c56756
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlinstalltranslator-function"></a>Функция SQLInstallTranslator
**Соответствия**  
 Появился в версии: ODBC 2.5, устаревшие  
  
 **Сводка**  
 В ODBC 3.0 **SQLInstallTranslator** будет заменен [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md). Вызовы **SQLInstallTranslator** будут сопоставлены с **SQLInstallTranslatorEx**. Дополнительные сведения см. в разделе **SQLInstallTranslatorEx**.  
  
 **SQLInstallTranslator** будет возвращаться значение FALSE, если приложение вызывает ее в ODBC 3 *.x* диспетчера драйверов с *lpszInfFile* аргументу присвоено значение, отличное от NULL. Файл Odbc.inf, используемый в ODBC 2. *x* больше не поддерживается в ODBC 3 *.x*, даже для обеспечения обратной совместимости.
