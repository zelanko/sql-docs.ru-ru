---
title: Международная поддержка (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50d65520e74a4e11bada88795fedc0b2f2e82628
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62471047"
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>Поддержка международного использования (драйвер ODBC для Visual FoxPro)
Драйвер ODBC Microsoft Visual FoxPro поддерживает:  
  
-   Двухбайтовые кодировки (DBCS)  
  
-   Несколько последовательностей упорядочивания  
  
 Определяет порядок сортировки *порядок сортировки* для данных, хранящихся в таблице Visual FoxPro или базы данных. По умолчанию драйвер настроен на использование упорядоченной последовательности, которые поддерживают языковую версию операционной системы.  
  
 Список поддерживаемых упорядоченной последовательности, см. в разделе [ЗАДАТЬ COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
## <a name="locale"></a>локаль  
 Набор данных, связанных с данного языка и страны или региона. Языковой стандарт указывает определенных параметров, например десятичные разделители, даты и форматы времени и порядок сортировки символьных.  
  
## <a name="sort-order"></a>порядок сортировки  
 Порядки сортировки включения правил сортировки различных *языкового стандарта*s, позволяют сортировать данные на этих языках правильно. В Visual FoxPro текущий порядок сортировки определяет результаты выражения символов и порядок, в котором записи будут представлены в индексированных или сортировки таблицы.
