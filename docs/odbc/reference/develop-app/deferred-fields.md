---
title: Отложенное поля | Документы Microsoft
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
- descriptors [ODBC], deferred fields
- deferred fields [ODBC]
ms.assetid: 5abeb9cc-4070-4f43-a80d-ad6a2004e5f3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 47e9d94d3a3f6e39864d27fee1c82f8e69f24b37
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="deferred-fields"></a>Отложенных полей
Значения *отложенных полей* не используются, когда они заданы, но драйвер сохраняет адреса переменных для отложенного эффекта. Для дескриптора параметра приложения, драйвер использует содержимое переменных во время вызова **SQLExecDirect** или **SQLExecute**. Для дескриптор строк приложения драйвер использует содержимое переменных во время выборки.  
  
 Ниже приведены отложенных полей.  
  
-   SQL_DESC_DATA_PTR и SQL_DESC_INDICATOR_PTR поля записи дескриптора.  
  
-   Поле SQL_DESC_OCTET_LENGTH_PTR записи дескриптор для этого приложения.  
  
-   В случае нескольких строк выборки SQL_DESC_ARRAY_STATUS_PTR и SQL_DESC_ROWS_PROCESSED_PTR поля заголовка дескриптора.  
  
 При выделении дескриптор отложенных полей каждой записи дескриптора иметь значение null. Смысл значения null выглядит следующим образом:  
  
-   Если SQL_DESC_ARRAY_STATUS_PTR имеет значение null, многострочные выборки не возвращает этого компонента диагностических данных в ряду.  
  
-   Если SQL_DESC_DATA_PTR имеет значение null, запись не связан.  
  
-   Если поле SQL_DESC_OCTET_LENGTH_PTR Отменить имеет значение null, драйвер не возвращает сведения о длине столбца.  
  
-   Если поле SQL_DESC_OCTET_LENGTH_PTR в APD имеет значение null, а параметр — строку символов, драйвер предполагает, что строка является символом null. Для вывода динамических параметров значение null в этом поле не позволяет драйвер возвращает сведения о длине. (Если параметр символьной строки не указывает на поле SQL_DESC_TYPE, SQL_DESC_OCTET_LENGTH_PTR поля учитывается.)  
  
 Приложение не должно освобождать или отменить переменных, используемых для отложенных полей между связывает их с полями и временем, драйвер считывает или записывает их.
