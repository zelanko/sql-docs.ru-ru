---
title: Копирование дескрипторы | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], copying
- copying descriptors [ODBC]
ms.assetid: 949a860d-6579-4218-882e-8c061688dd87
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d5a09d56193641e899ebe64d5bfb455a06af902f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="copying-descriptors"></a>Копирование дескрипторов
**SQLCopyDesc** функция вызывается для копирования поля один дескриптор другим дескриптором. Поля могут быть скопированы только дескриптор приложения или IPD, но не IRD. Поля могут быть скопированы из любого типа дескриптора. Копируются только те поля, которые определены для исходной и целевой дескрипторы. **SQLCopyDesc** не копирует поле SQL_DESC_ALLOC_TYPE, так как не удалось изменить тип выделения дескриптора. Скопированные поля перезаписать существующие поля.  
  
 Отменить дескриптором одной инструкции можно использовать в качестве APD другой дескриптором инструкции. Это позволяет приложению нужно скопировать строки между таблицами без копирования данных на уровне приложения. Для этого дескриптора строки, который описывает выбранной строки таблицы повторно используется в качестве дескриптор параметра для параметра в инструкции INSERT. Тип сведений SQL_MAX_CONCURRENT_ACTIVITIES должен быть больше 1 для выполнения данной операции.
