---
title: "Копирование дескрипторы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], copying
- copying descriptors [ODBC]
ms.assetid: 949a860d-6579-4218-882e-8c061688dd87
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8cd2ea29713d3bf1e05e76de21397f71dd30c824
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="copying-descriptors"></a>Копирование дескрипторов
**SQLCopyDesc** функция вызывается для копирования поля один дескриптор другим дескриптором. Поля могут быть скопированы только дескриптор приложения или IPD, но не IRD. Поля могут быть скопированы из любого типа дескриптора. Копируются только те поля, которые определены для исходной и целевой дескрипторы. **SQLCopyDesc** не копирует поле SQL_DESC_ALLOC_TYPE, так как не удалось изменить тип выделения дескриптора. Скопированные поля перезаписать существующие поля.  
  
 Отменить дескриптором одной инструкции можно использовать в качестве APD другой дескриптором инструкции. Это позволяет приложению нужно скопировать строки между таблицами без копирования данных на уровне приложения. Для этого дескриптора строки, который описывает выбранной строки таблицы повторно используется в качестве дескриптор параметра для параметра в инструкции INSERT. Тип сведений SQL_MAX_CONCURRENT_ACTIVITIES должен быть больше 1 для выполнения данной операции.
