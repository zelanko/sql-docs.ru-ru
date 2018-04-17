---
title: Международная поддержка (драйвер ODBC для Visual FoxPro) | Документы Microsoft
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
- double-byte character sets [ODBC]
- FoxPro ODBC driver [ODBC], international support
- DBCS [ODBC]
- international support [ODBC]
- sort order [ODBC]
- collating sequences [ODBC]
- Visual FoxPro ODBC driver [ODBC], international support
ms.assetid: cd3fab32-13f1-4a86-abc4-5e18667669fc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 37287933ba143441023303e8aad2755042b29176
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>Международная поддержка (драйвер ODBC для Visual FoxPro)
Драйвер ODBC Microsoft Visual FoxPro поддерживает.  
  
-   Двухбайтовые кодировки (DBCS)  
  
-   Несколько упорядоченной последовательности  
  
 Определяет порядок сортировки *порядок сортировки* для данных, хранящихся в таблице Visual FoxPro или базы данных. По умолчанию драйвер настроен на использование упорядоченной последовательности, которые поддерживают языковую версию операционной системы.  
  
 Список поддерживаемых упорядоченной последовательности см. в разделе [ЗАДАТЬ COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
## <a name="locale"></a>локаль  
 Набор данных, связанных с данного языка и страны или региона. Языковой стандарт указывает определенные параметры, такие как десятичные разделители, даты и форматы времени и порядок сортировки символьных.  
  
## <a name="sort-order"></a>порядок сортировки  
 Порядки сортировки включить правила сортировки различных *языкового стандарта*s, позволяя правильно сортировать данные на этих языках. В Visual FoxPro текущий порядок сортировки определяет результаты выражения символов и порядок, в котором отображаются записи в индексированных или сортировки таблицы.
