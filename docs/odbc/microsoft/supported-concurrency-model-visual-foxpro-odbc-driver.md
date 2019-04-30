---
title: Поддерживается модель параллелизма (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], concurrency
- concurrency models [ODBC]
- FoxPro ODBC driver [ODBC], concurrency
ms.assetid: c39ed963-3af1-4888-8631-6083692ddcd7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8528ecb2f34d3f0ef7120c7047865ab5f6c1a72
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270100"
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>Поддерживаемая модель параллелизма (драйвер ODBC для Visual FoxPro)
Драйвер ODBC для Visual FoxPro поддерживает *параллелизма только для чтения*. Приложение может вызвать [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) с параметром SQL_CONCURRENCY SQL_CONCUR_READ_ONLY.  
  
 Дополнительные сведения см. в разделе [Справочник по программированию ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="read-only-concurrency"></a>параллелизма только для чтения  
 Не удается обновить курсор.  
  
## <a name="row-versioning"></a>управление версиями строк  
 По сути timestamp поддержки, в котором строка версии сравниваются во время обновления.
