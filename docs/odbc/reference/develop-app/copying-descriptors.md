---
title: Копирование дескрипторов Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], copying
- copying descriptors [ODBC]
ms.assetid: 949a860d-6579-4218-882e-8c061688dd87
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2e2e5897afc3673a21396e256df04d25008c8cdf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301673"
---
# <a name="copying-descriptors"></a>Копирование дескрипторов
Функция **S'LCopyDesc** называется копированием полей одного дескриптора другому дескриптору. Поля могут быть скопированы только на дескриптор приложения или IPD, но не в IRD. Поля можно скопировать с любого типа дескриптора. Копируются только те поля, которые определены как для источника, так и для целевых дескрипторов. **S'LCopyDesc** не копирует SQL_DESC_ALLOC_TYPE поле, так как тип распределения дескриптора не может быть изменен. Копированные поля перезаписывают существующие поля.  
  
 ARD на одной ручке оператора может служить APD на другой ручке оператора. Это позволяет приложению копировать строки между таблицами без копирования данных на уровне приложения. Для этого дескриптор строки, описывающий извлеченный ряд таблицы, повторно используется в качестве описательного параметра для параметра в заявлении INSERT. Для успеха этой операции SQL_MAX_CONCURRENT_ACTIVITIES тип информации должен быть больше 1.
