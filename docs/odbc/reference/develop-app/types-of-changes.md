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
ms.openlocfilehash: ca1b0fc2f7a1a74e1b9ab9a85baba945e4edf491
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792953"
---
# <a name="types-of-changes"></a>Типы изменений
Три типа изменения вносятся в ODBC *3.x* (и какая-либо версия ODBC). Каждый из них по-разному влияет на обратной совместимости и обрабатывается по-разному. Эти изменения описаны в следующей таблице.  
  
|Тип изменения|Описание|  
|--------------------|-----------------|  
|Новые возможности|Это возможности, которые не знакомы с ODBC *3.x*, например привязки вне строки или дескрипторов. Они реализованы только в том случае, если приложение и драйверов, а также диспетчера драйверов, имеют версии *3.x*, поэтому не выполняется, чтобы сделать эти обладает обратной совместимостью.|  
|Повторяющийся функции|Это возможности, которые существуют в ODBC *2.x* и ODBC *3.x* , но реализуются по-разному в каждом. Функции **SQLAllocHandle** и **SQLAllocStmt** являются примерами. Обратная совместимость выдает для этих и других повторяющийся функции, главным образом обрабатываются сопоставления диспетчера драйверов.|  
|Изменения в поведении|Это возможности, которые обрабатываются по-разному в ODBC *2.x* и ODBC *3.x*. Значение типа datetime **#define** является примером. Эти функции обрабатываются ODBC *3.x* драйвер на основании атрибута настройку среды. (См. в разделе [изменения в поведении](../../../odbc/reference/develop-app/behavioral-changes.md) подробнее.)|
