---
description: Отложенные поля
title: Отложенные поля | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], deferred fields
- deferred fields [ODBC]
ms.assetid: 5abeb9cc-4070-4f43-a80d-ad6a2004e5f3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f8b313f2d77270e95830de1a524706aa7fe36e33
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424696"
---
# <a name="deferred-fields"></a>Отложенные поля
Значения *отложенных полей* не используются, если они заданы, но драйвер сохраняет адреса переменных для отложенного действия. Для дескриптора параметра приложения драйвер использует содержимое переменных во время вызова **SQLExecDirect** или **SQLExecute**. Для дескриптора строки приложения драйвер использует содержимое переменных во время выборки.  
  
 Ниже приведены отложенные поля.  
  
-   Поля SQL_DESC_DATA_PTR и SQL_DESC_INDICATOR_PTR записи дескриптора.  
  
-   SQL_DESC_OCTET_LENGTH_PTR поле записи дескриптора приложения.  
  
-   В случае многострочные FETCH поля SQL_DESC_ARRAY_STATUS_PTR и SQL_DESC_ROWS_PROCESSED_PTR заголовка дескриптора.  
  
 При выделении дескриптора отложенные поля каждой записи дескриптора изначально имеют значение null. Значение null имеет следующий вид:  
  
-   Если SQL_DESC_ARRAY_STATUS_PTR имеет значение null, многострочные FETCH не может вернуть этот компонент диагностической информации по строке.  
  
-   Если SQL_DESC_DATA_PTR имеет значение null, запись не привязана.  
  
-   Если поле SQL_DESC_OCTET_LENGTH_PTR АРД имеет значение null, драйвер не возвращает сведения о длине для этого столбца.  
  
-   Если поле SQL_DESC_OCTET_LENGTH_PTR APD имеет значение null, а параметр является символьной строкой, драйвер предполагает, что строка завершается нулем. Для выходных динамических параметров значение NULL в этом поле предотвращает возврат сведений о длине драйвером. (Если поле SQL_DESC_TYPE не указывает параметр символьной строки, поле SQL_DESC_OCTET_LENGTH_PTR игнорируется.)  
  
 Приложение не должно освобождать или удалять переменные, используемые для отложенных полей, между моментом, когда он связывает их с полями, и временем, которое драйвер считывает или записывает.
