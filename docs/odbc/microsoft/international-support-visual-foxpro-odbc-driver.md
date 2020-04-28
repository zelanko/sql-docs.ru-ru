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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b4b0c758bb478ea6a468e6756c3d6f0f52c766f5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299974"
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>Поддержка международного использования (драйвер ODBC для Visual FoxPro)
Драйвер ODBC для Microsoft Visual FoxPro поддерживает:  
  
-   Двухбайтовые кодировки (DBCS)  
  
-   Несколько последовательностей сортировки  
  
 Последовательность сортировки определяет *порядок сортировки* данных, хранящихся в таблице или базе данных Visual FoxPro. По умолчанию драйвер настроен на использование последовательностей сортировки, поддерживающих языковую версию операционной системы.  
  
 Список поддерживаемых последовательностей сортировки см. в разделе [Set COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
## <a name="locale"></a>локаль  
 Набор сведений, соответствующий данному языку и стране или региону. Языковой стандарт определяет определенные параметры, такие как десятичные разделители, форматы даты и времени, а также порядок сортировки символов.  
  
## <a name="sort-order"></a>порядок сортировки  
 Порядок сортировки включает правила сортировки различных *языковых стандартов*, что позволяет правильно сортировать данные на этих языках. В Visual FoxPro текущий порядок сортировки определяет результаты сравнения символьных выражений и порядок, в котором записи отображаются в индексированных или отсортированных таблицах.
