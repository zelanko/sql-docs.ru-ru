---
title: "SQLGetData и блочных курсоров | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursors [ODBC], block
- SQLGetData function [ODBC], block cursors
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 12599cdc-7725-4faf-bcae-e163ea0f5851
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 715e521f5c8ee5e578ee7a21dd324d3dfb2bb239
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData и блочных курсоров
**SQLGetData** работает для одного столбца из одной строки и не удалось извлечь массив, содержащий данные из нескольких строк. Это так, как использовать основной **SQLGetData** — выборка данных long в части, и почти или совсем нет причин для этого для более чем одной строке за раз.  
  
 Для использования **SQLGetData** с блочными, приложение сначала вызывает **SQLSetPos** для позиционирования курсора на одну строку. Затем он вызывает **SQLGetData** для столбца в этой строке. Однако такое поведение является необязательным. Чтобы определить, что драйвер поддерживает использование **SQLGetData** с блочных курсоров, приложение вызывает **SQLGetInfo** с параметром SQL_GETDATA_EXTENSIONS.

