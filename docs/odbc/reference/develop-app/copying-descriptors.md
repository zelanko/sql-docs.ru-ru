---
title: Копирование дескрипторов | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da22ba86ea49532f460b081b13e18d6b7d95211c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63042760"
---
# <a name="copying-descriptors"></a>Копирование дескрипторов
**SQLCopyDesc** функция вызывается для копирования поля один дескриптор другим дескриптором. Поля могут быть скопированы только дескриптор приложений или IPD, но не IRD. Поля можно скопировать из любого типа дескриптора. Копируются только поля, которые определены для исходной и целевой дескрипторов. **SQLCopyDesc** не копирует поле SQL_DESC_ALLOC_TYPE, поскольку невозможно изменить тип выделения дескриптора. Скопированные поля перезаписывают существующие поля.  
  
 Отменить дескриптором одной инструкции можно использовать в качестве APD другим дескриптором инструкции. Это позволяет приложению нужно скопировать строки между таблицами без копирования данных на уровне приложения. Чтобы сделать это, повторно дескриптор строки, который описывает выбранной строки таблицы используется как дескриптор параметра для параметра в инструкции INSERT. Тип сведений SQL_MAX_CONCURRENT_ACTIVITIES должен быть больше 1 для выполнения данной операции.
