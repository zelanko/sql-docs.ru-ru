---
title: Поддерживаемая модель параллелизма (Visual FoxPro ODBC Driver) Документы Майкрософт
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
ms.openlocfilehash: 253a6dd86f6dc974d53dd151636bb8b8132e4d02
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307720"
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>Поддерживаемая модель параллелизма (драйвер ODBC для Visual FoxPro)
Визуальный Водитель FoxPro ODBC поддерживает *только для чтения параллелизм.* Ваше приложение может позвонить по [телефону s'LSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) с SQL_CONCURRENCY опцией SQL_CONCUR_READ_ONLY.  
  
 Для получения дополнительной [информации](../../odbc/reference/odbc-programmer-s-reference.md)см.  
  
## <a name="read-only-concurrency"></a>только для чтения параллелизм  
 Курсор не может быть обновлен.  
  
## <a name="row-versioning"></a>управление версиями строк  
 По существу поддержка метки времени, в которой версии строк сравниваются во время обновления.
