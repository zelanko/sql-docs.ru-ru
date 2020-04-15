---
title: Передача данных в двоичной форме Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], transferring in binary form
- transferring data in binary form [ODBC]
- binary data transfers [ODBC]
ms.assetid: 4b12a9de-51d0-416a-87f4-9bf84959cad9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 53531ff4a3b2e1441fabf22ec7a3ce12b15540eb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301416"
---
# <a name="transferring-data-in-its-binary-form"></a>Передача данных в двоичной форме
Приложение может безопасно передавать данные (во внутренней форме, используемой указанным DBMS) между двумя источниками данных, которые используют ту же DBMS и аппаратную платформу. Для данной части данных типы данных S'L должны быть одинаковыми в источниках и целевых источниках данных. Тип данных C является SQL_C_BINARY.  
  
 Когда приложение вызывает **S'LFetch,** **S'LFetchScroll**, или **S'LGetData** для извлечения данных из источника данных, драйвер извлекает данные из источника данных и передает их, без преобразования, в место хранения типа SQL_C_BINARY. Когда приложение вызывает **s'LBulkOperations,** **S'LExecute,** **S'LExecDirect**, **S'LPutData или S'LSetPos** для отправки данных в целевой источник данных, водитель изыскивает данные из места хранения и передает их без преобразования в целевой источник данных.  
  
> [!NOTE]  
>  Приложения, которые передают любые данные (кроме двоичных данных) таким образом, не совместимы между DBMS.  
  
 **Для** копирования привязок строк от исходного DBMS к парабищам в целевом DBMS можно использовать привязки строк.
