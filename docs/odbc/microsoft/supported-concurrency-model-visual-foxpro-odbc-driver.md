---
description: Поддерживаемая модель параллелизма (драйвер ODBC для Visual FoxPro)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1be0a7e9ea3700941282f23956a8c304a1ef7f5e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500107"
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>Поддерживаемая модель параллелизма (драйвер ODBC для Visual FoxPro)
Драйвер ODBC для Visual FoxPro поддерживает *параллелизм только для чтения*. Приложение может вызвать [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) с параметром SQL_CONCURRENCY SQL_CONCUR_READ_ONLY.  
  
 Дополнительные сведения см. в [справочнике программиста по ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="read-only-concurrency"></a>параллелизм только для чтения  
 Не удается обновить курсор.  
  
## <a name="row-versioning"></a>управление версиями строк  
 По сути, поддержка меток времени, при которой версии строк сравниваются во время обновления.
