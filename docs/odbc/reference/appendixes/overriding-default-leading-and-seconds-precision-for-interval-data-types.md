---
title: Переопределение ведущих и секунд точность для интервала типов данных (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- precision [ODBC], interval data types
- seconds precision [ODBC]
- interval data type [ODBC], precision
- interval leading precision [ODBC]
- interval precision [ODBC]
ms.assetid: 3d65493f-dce7-4d29-9f59-c63a4e47918c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1e60d5d8fc696ad8e2bd4cfb0c082ff214e066d0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303605"
---
# <a name="overriding-default-leading-and-seconds-precision-for-interval-data-types"></a>Переопределение заданной по умолчанию точности ведущего значения и точности значения долей секунды для интервальных типов данных
Когда SQL_DESC_TYPE поле ARD устанавливается в тип даты или интервалc C, позвонив либо по телефону **S'LBindCol,** либо **s'LSetDescField**, SQL_DESC_PRECISION поле (которое содержит точность интервалных секунд) устанавливается по следующим значениям:  
  
-   6 для метки времени и всех типов интервальных данных со вторым компонентом.  
  
-   0 для всех других типов данных.  
  
 Для всех типов интервальных данных поле SQL_DESC_DATETIME_INTERVAL_PRECISION дескриптора, содержащее точность поля интервала, настроено на значение по умолчанию 2.  
  
 Когда SQL_DESC_TYPE поле в APD устанавливается в тип дата или интервал C, позвонив либо по телефону, либо **s'LBindParameter** или **S'LSetDesccField,** SQL_DESC_PRECISION и SQL_DESC_DATETIME_INTERVAL_PRECISION поля в APD устанавливаются по умолчанию, приведенным ранее. Это верно для параметров ввода, но не для входных/выходных или выходных параметров.  
  
 Вызов в **S'LSetDescCRec** устанавливает точность интервала, ведущую к по умолчанию, но устанавливает точность интервалных секунд (в поле SQL_DESC_PRECISION) к значению аргумента *точности.*  
  
 Если любой из приведенных ранее по умолчанию не приемлем для приложения, приложение должно установить SQL_DESC_PRECISION или SQL_DESC_DATETIME_INTERVAL_PRECISION поле, позвонив по **s'LSetDescField**.  
  
 Если приложение вызывает **S'LGetData** для возврата данных в тип даты или интервал C, используется точность интервала по умолчанию и точность интервалных секунд. Если любой из них не приемлем по умолчанию, приложение должно вызвать **S'LSetDescField,** чтобы установить поле дескриптора, либо **s'LSetDesccRec,** чтобы установить SQL_DESC_PRECISION. Вызов на **S'LGetData** должен иметь *TargetType* SQL_ARD_TYPE использовать значения в полях дескрипторов.  
  
 При вызове **S'LPutData** точность интервала, ведущая точность и точность интервалных секунд, считываются с полей записи дескриптора, которые соответствуют параметру данных по исполнению или столбцу, которые являются полями APD для вызовов в **S'LExecute** или **S'LExecDirect**, или поля ARD для вызовов на **S'LBulkOperations** или **S'LSetPos.**
