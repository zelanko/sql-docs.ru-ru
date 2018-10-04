---
title: Сопоставление SQLColAttributes | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], mapping
ms.assetid: 30e25719-176b-4c48-97d4-920766b22412
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d0332e38a96d17589d9aa75bfe2a3c918dcc78d2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47639652"
---
# <a name="sqlcolattributes-mapping"></a>Сопоставление SQLColAttributes
Если приложение вызывает **SQLColAttributes** через ODBC 3 *.x* драйвера, вызов **SQLColAttributes** сопоставляется **SQLColAttribute** следующим образом:  
  
> [!NOTE]  
>  Префикс, используемый в *FieldIdentifier* значения в ODBC 3 *.x* было изменено с, используемых в ODBC 2. *x*. Новый префикс — «SQL_DESC»; старый префикс был «SQL_COLUMN».  
  
1.  Если приложение ODBC 2. *x* приложения, *fDescType* является SQL_COLUMN_TYPE и возвращаемый тип является кратким типом DATETIME, диспетчер драйверов карты, возвращаемые значения для кодов date, time и timestamp.  
  
2.  Если *fDescType* SQL_COLUMN_NAME, SQL_COLUMN_NULLABLE или SQL_COLUMN_COUNT, диспетчер драйверов вызывает **SQLColAttribute** в драйвере с *FieldIdentifier* аргумент сопоставляется SQL_DESC_NAME, SQL_DESC_NULLABLE или SQL_DESC_COUNT, соответствующим образом *.* Все остальные значения *fDescType* передаются через драйвер.  
  
 ODBC 3 *.x* драйвер должен поддерживать все ODBC 3 *.x* *FieldIdentifiers* для **SQLColAttribute**.  
  
 ODBC 3 *.x* драйвер должен поддерживать SQL_COLUMN_PRECISION и SQL_DESC_PRECISION, SQL_COLUMN_SCALE и SQL_DESC_SCALE и SQL_COLUMN_LENGTH и SQL_DESC_LENGTH. Эти значения отличаются, так как точность, масштаб и длина определяются по-другому в ODBC 3 *.x* в ODBC 2. *x*. Дополнительные сведения см. в разделе [размер столбца, десятичных разрядов, длительность октета передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в типах данных приложение D:.
