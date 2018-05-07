---
title: Сопоставление SQLColAttributes | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], mapping
ms.assetid: 30e25719-176b-4c48-97d4-920766b22412
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b87311d3b913395fb0529392c7bc4ed9cc93024e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlcolattributes-mapping"></a>Сопоставление SQLColAttributes
Если приложение вызывает **SQLColAttributes** через ODBC 3 *.x* драйвера, вызов **SQLColAttributes** сопоставляется **SQLColAttribute** следующим образом:  
  
> [!NOTE]  
>  Префикс, используемый в *FieldIdentifier* значения в ODBC 3 *.x* было изменено с, используемых в ODBC 2. *x*. Новый префикс — «SQL_DESC»; старый префикс был «SQL_COLUMN».  
  
1.  Если приложение ODBC 2. *x* приложения, *fDescType* является SQL_COLUMN_TYPE, и возвращаемый тип четкими типа DATETIME, диспетчер драйверов maps, возвращаемые значения для кодов даты, времени и отметок времени.  
  
2.  Если *fDescType* SQL_COLUMN_NAME, SQL_COLUMN_NULLABLE или SQL_COLUMN_COUNT, диспетчер драйверов вызывает **SQLColAttribute** в драйвере с *FieldIdentifier* аргумент сопоставляется SQL_DESC_NAME, SQL_DESC_NULLABLE или SQL_DESC_COUNT, соответствующим образом *.* Все остальные значения *fDescType* передаются через драйвер.  
  
 ODBC 3 *.x* драйвер должен поддерживать все функции ODBC 3 *.x* *FieldIdentifiers* для **SQLColAttribute**.  
  
 ODBC 3 *.x* драйвер должен поддерживать SQL_COLUMN_PRECISION и SQL_DESC_PRECISION, SQL_COLUMN_SCALE и SQL_DESC_SCALE и SQL_COLUMN_LENGTH и SQL_DESC_LENGTH. Эти значения не совпадают, так как точность, масштаб и длина определяются по-другому в ODBC 3 *.x* чем были в ODBC 2. *x*. Дополнительные сведения см. в разделе [размер столбца, десятичных цифр, длина в октетах передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в типах данных приложение D:.
