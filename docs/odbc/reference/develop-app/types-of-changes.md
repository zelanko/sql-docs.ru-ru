---
title: Типы изменений | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], types of changes
- backward compatibility [ODBC], types of changes
ms.assetid: 6a7db81a-20aa-4915-aed8-429711a36f49
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac92c6d40ea9ead6b8875e3338bb740b4bdf8523
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47631822"
---
# <a name="types-of-changes"></a>Типы изменений
Три типа изменения вносятся в ODBC 3. *x* (и какая-либо версия ODBC). Каждый из них по-разному влияет на обратной совместимости и обрабатывается по-разному. Эти изменения описаны в следующей таблице.  
  
|Тип изменения|Описание|  
|--------------------|-----------------|  
|Новые возможности|Это возможности появились в ODBC 3. *x*, например привязки вне строки или дескрипторов. Они реализованы только в том случае, если приложение и драйверов, а также диспетчера драйверов, имеют версии 3 *.x*, поэтому не выполняется, чтобы сделать эти обладает обратной совместимостью.|  
|Повторяющийся функции|Это возможности, которые существуют в ODBC 2 *.x* а ODBC 3. *x* , но реализуются по-разному в каждом. Функции **SQLAllocHandle** и **SQLAllocStmt** являются примерами. Обратная совместимость выдает для этих и других повторяющийся функции, главным образом обрабатываются сопоставления диспетчера драйверов.|  
|Изменения в поведении|Это возможности, которые обрабатываются по-разному в ODBC 2 *.x* а ODBC 3. *x*. Значение типа datetime **#define** является примером. Эти функции обрабатываются ODBC 3. *x* драйвер на основании атрибута настройку среды. (См. в разделе [изменения в поведении](../../../odbc/reference/develop-app/behavioral-changes.md) подробнее.)|
