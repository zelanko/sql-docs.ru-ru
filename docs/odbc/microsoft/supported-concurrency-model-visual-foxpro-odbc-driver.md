---
title: Поддерживается модель параллелизма (драйвер ODBC для Visual FoxPro) | Документы Microsoft
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
- Visual FoxPro ODBC driver [ODBC], concurrency
- concurrency models [ODBC]
- FoxPro ODBC driver [ODBC], concurrency
ms.assetid: c39ed963-3af1-4888-8631-6083692ddcd7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18f555f32ed05914d325ba4664e952d4488f787b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>Модель поддерживается параллелизма (драйвер ODBC для Visual FoxPro)
Драйвер ODBC для Visual FoxPro поддерживает *параллелизма только для чтения*. Приложение может вызвать [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) с параметром SQL_CONCURRENCY SQL_CONCUR_READ_ONLY.  
  
 Дополнительные сведения см. в разделе [справочнике программиста ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="read-only-concurrency"></a>параллелизма только для чтения  
 Не удается обновить курсора.  
  
## <a name="row-versioning"></a>управление версиями строк  
 По существу timestamp поддержки, сравнения версий строк во время обновления.
