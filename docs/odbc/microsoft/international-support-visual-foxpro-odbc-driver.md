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
ms.openlocfilehash: e987c224f2d716fcab3bf898b1cb276e922e48ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68085506"
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>Поддержка международного использования (драйвер ODBC для Visual FoxPro)
Драйвер ODBC для Microsoft Visual FoxPro поддерживает:  
  
-   Двухбайтовые кодировки (DBCS)  
  
-   Несколько последовательностей сортировки  
  
 Последовательность сортировки определяет *порядок сортировки* данных, хранящихся в таблице или базе данных Visual FoxPro. По умолчанию драйвер настроен на использование последовательностей сортировки, поддерживающих языковую версию операционной системы.  
  
 Список поддерживаемых последовательностей сортировки см. в разделе [Set COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
## <a name="locale"></a>местность  
 Набор сведений, соответствующий данному языку и стране или региону. Языковой стандарт определяет определенные параметры, такие как десятичные разделители, форматы даты и времени, а также порядок сортировки символов.  
  
## <a name="sort-order"></a>порядок сортировки  
 Порядок сортировки включает правила сортировки различных *языковых стандартов*, что позволяет правильно сортировать данные на этих языках. В Visual FoxPro текущий порядок сортировки определяет результаты сравнения символьных выражений и порядок, в котором записи отображаются в индексированных или отсортированных таблицах.
