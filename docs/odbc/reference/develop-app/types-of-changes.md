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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f44adb59aa9b0f25475a76a97fe3670de0228c08
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301609"
---
# <a name="types-of-changes"></a>Типы изменений
В ODBC *3. x* (и любой версии ODBC) вносятся изменения трех типов. Каждое из них влияет на обратную совместимость по-разному и обрабатывается другим способом. Эти изменения описаны в следующей таблице.  
  
|Тип изменения|Описание|  
|--------------------|-----------------|  
|Новые функции|Это новые функции ODBC *3. x*, такие как нелинейная привязка или дескрипторы. Они реализуются только в том случае, если приложение и драйвер, а также диспетчер драйверов имеют версию *3. x*, поэтому нет никаких попыток сделать эти данные обратно совместимыми.|  
|Дублирование компонентов|Это функции, которые существуют в ODBC *2. x* и ODBC *3. x* , но реализуются различными способами в каждом. Примерами являются функции **функцию SQLAllocHandle** и **SQLAllocStmt** . Проблемы обратной совместимости для этих и других повторяющихся компонентов в основном обрабатываются сопоставлениями в диспетчере драйверов.|  
|Изменения в поведении|Это функции, которые обрабатываются по-разному в ODBC *2. x* и ODBC *3. x*. Примером является **#define** DateTime. Эти функции обрабатываются драйвером ODBC *3. x* на основе параметра атрибута среды. (Дополнительные сведения см. в разделе [изменения поведения](../../../odbc/reference/develop-app/behavioral-changes.md) .)|
