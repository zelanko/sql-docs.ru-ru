---
title: Международная поддержка (Visual FoxPro ODBC Драйвер) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- double-byte character sets [ODBC]
- FoxPro ODBC driver [ODBC], international support
- DBCS [ODBC]
- international support [ODBC]
- sort order [ODBC]
- collating sequences [ODBC]
- Visual FoxPro ODBC driver [ODBC], international support
ms.assetid: cd3fab32-13f1-4a86-abc4-5e18667669fc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b4b0c758bb478ea6a468e6756c3d6f0f52c766f5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299974"
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>Поддержка международного использования (драйвер ODBC для Visual FoxPro)
Microsoft Visual FoxPro ODBC Драйвер поддерживает:  
  
-   Наборы символов с двойным байтом (DBCS)  
  
-   Несколько последовательностей сопоставления  
  
 Последовательность сопоставления определяет *порядок сортировки* данных, хранящихся в таблице или базе данных Visual FoxPro. По умолчанию драйвер настроен на использование последовательностей, поддерживающих языковую версию операционной системы.  
  
 Список поддерживаемых последовательностей сопоставления см. [SET COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
## <a name="locale"></a>локаль  
 Набор информации, соответствующей данному языку и стране/региону. Локали указывает определенные параметры, такие как десятичные сепараторы, форматы даты и времени, а также порядок сортировки символов.  
  
## <a name="sort-order"></a>порядок сортировки  
 Сортировать заказы включают правила сортировки различных *языков,* что позволяет правильно сортировать данные на этих языках. В Visual FoxPro текущий порядок сортировки определяет результаты сравнения выражений символов и порядок, в котором записи отображаются в индексированных или отсортированных таблицах.
