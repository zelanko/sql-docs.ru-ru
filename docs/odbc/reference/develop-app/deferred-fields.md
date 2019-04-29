---
title: Отложенное поля | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c7800e7da867b4eb0c34fa3feeba5edb2d41cd6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63049876"
---
# <a name="deferred-fields"></a>Отложенные поля
Значения *отложенного поля* не используются, когда они заданы, но драйвер сохраняет адреса переменных для отложенного создания эффекта. Для дескриптора параметра приложения, драйвер использует значения переменных во время вызова **SQLExecDirect** или **SQLExecute**. Для дескриптор строки приложения драйвер использует значения переменных во время выборки.  
  
 Ниже приведены отложенных полей.  
  
-   SQL_DESC_DATA_PTR и SQL_DESC_INDICATOR_PTR поля запись дескриптора.  
  
-   Поле SQL_DESC_OCTET_LENGTH_PTR записи дескриптора для этого приложения.  
  
-   В случае с несколькими строками fetch SQL_DESC_ARRAY_STATUS_PTR и SQL_DESC_ROWS_PROCESSED_PTR поля заголовка дескриптора.  
  
 При выделении дескриптор отложенных полей каждой записи дескриптора изначально будет иметь значение null. Значение null значение выглядит следующим образом:  
  
-   Если SQL_DESC_ARRAY_STATUS_PTR имеет значение null, многострочные fetch не возвращает этот компонент диагностических сведений строки.  
  
-   Если SQL_DESC_DATA_PTR имеет значение null, запись не связан.  
  
-   Если поле SQL_DESC_OCTET_LENGTH_PTR Отменить имеет значение null, драйвер не возвращает сведения о длине столбца.  
  
-   Если параметр представляет собой строку символов, поле SQL_DESC_OCTET_LENGTH_PTR в APD имеет значение null, драйвер предполагает, что строка заканчивается нулевым байтом. Для динамических параметров выходных данных значение null в этом поле предотвращает драйвер возвращал сведения о длине. (Если поле SQL_DESC_TYPE не указывает на параметр символьной строки, учитывается поле SQL_DESC_OCTET_LENGTH_PTR).  
  
 Приложение не должно deallocate или отменить переменных, используемых для отложенных полей между временем связывает их с полями и времени, драйвер считывает или записывает их.
