---
title: SQLGetData и блочных курсоров | Документы Microsoft
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
- cursors [ODBC], block
- SQLGetData function [ODBC], block cursors
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 12599cdc-7725-4faf-bcae-e163ea0f5851
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 29b41623fe5f4681401e9726adbc1b0993ef98b4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData и блочных курсоров
**SQLGetData** работает для одного столбца из одной строки и не удалось извлечь массив, содержащий данные из нескольких строк. Это так, как использовать основной **SQLGetData** — выборка данных long в части, и почти или совсем нет причин для этого для более чем одной строке за раз.  
  
 Для использования **SQLGetData** с блочными, приложение сначала вызывает **SQLSetPos** для позиционирования курсора на одну строку. Затем он вызывает **SQLGetData** для столбца в этой строке. Однако такое поведение является необязательным. Чтобы определить, что драйвер поддерживает использование **SQLGetData** с блочных курсоров, приложение вызывает **SQLGetInfo** с параметром SQL_GETDATA_EXTENSIONS.
