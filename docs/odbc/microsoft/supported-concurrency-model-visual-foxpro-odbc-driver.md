---
title: Поддерживаемая модель параллелизма (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
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
ms.openlocfilehash: 597d1022fa6946e0ae768cb9600a3f4534c67a25
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68080695"
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>Поддерживаемая модель параллелизма (драйвер ODBC для Visual FoxPro)
Драйвер ODBC для Visual FoxPro поддерживает *параллелизм только для чтения*. Приложение может вызвать [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) с параметром SQL_CONCURRENCY SQL_CONCUR_READ_ONLY.  
  
 Дополнительные сведения см. в [справочнике программиста по ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="read-only-concurrency"></a>параллелизм только для чтения  
 Не удается обновить курсор.  
  
## <a name="row-versioning"></a>управление версиями строк  
 По сути, поддержка меток времени, при которой версии строк сравниваются во время обновления.
