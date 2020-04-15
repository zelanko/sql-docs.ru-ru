---
title: Переопределение точности и масштабирования по умолчанию для типов численных данных (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- numeric data type [ODBC], precision and scale
- precision [ODBC], numeric data types
- data types [ODBC], numeric data types
- numeric data type [ODBC]
- numeric literals [ODBC]
ms.assetid: 84292334-0e33-4a1b-84de-8c018dd787f3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 365c5f69d21dd3a4ad8e89805d81f1b3b0c9dcba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303595"
---
# <a name="overriding-default-precision-and-scale-for-numeric-data-types"></a>Переопределение заданных по умолчанию точности и шкалы для числовых типов данных
Когда поле SQL_DESC_TYPE в ARD настроено на SQL_C_NUMERIC, позвонив либо по телефону, либо **s'LBindCol,** либо **s'LSetDescField,** поле SQL_DESC_SCALE в ARD настроено на 0, а поле SQL_DESC_PRECISION настроено на точность по умолчанию, определяемую драйвером. Это также верно, когда поле SQL_DESC_TYPE в APD установлен на SQL_C_NUMERIC, позвонив либо **S'LBindParameter** или **S'LSetDescfield**. Это относится к параметрам ввода, ввода/вывода или вывода.  
  
 Если любой из описанных ранее по умолчанию не приемлем для приложения, приложение должно установить SQL_DESC_SCALE или SQL_DESC_PRECISION поле, позвонив по **s'LSetDescfield** или **S'LSetDescRec.**  
  
 Если приложение вызывает **S'LGetData** для возвращения данных в SQL_C_NUMERIC структуру, используются SQL_DESC_SCALE по умолчанию и SQL_DESC_PRECISION поля. Если по умолчанию они неприемлемы, приложение должно вызвать **S'LSetDesccRec** или **S'LSetDesccField,** чтобы установить поля, а затем вызвать **S'LGetData** с *помощью TargetType* SQL_ARD_TYPE использовать значения в полях дескриптора.  
  
 При вызове **s'LPutData** в вызове используется SQL_DESC_SCALE и SQL_DESC_PRECISION поля записи дескриптора, которые соответствуют параметру данных по исполнению или столбцу, которые являются полями APD для вызовов в **S'LExecute** или **S'LExecDirect,** или ARD поля для вызовов в **S'LBulkOperations** или **S'LSetPos.**
