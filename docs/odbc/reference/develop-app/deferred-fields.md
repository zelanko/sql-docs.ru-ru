---
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
ms.openlocfilehash: 094aba353e10ed568e1959b1d655109296507dee
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305975"
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
