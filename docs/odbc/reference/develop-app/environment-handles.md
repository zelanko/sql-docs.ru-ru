---
title: Дескрипторы среды | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment handles [ODBC]
- handles [ODBC], environment
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a73ec4a842e220a16189f1390df167fe12bbab8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692262"
---
# <a name="environment-handles"></a>Дескрипторы среды
*Среды* — это глобальный контекст, в котором для доступа к данным; связанные со средой, — это все данные, которые имеют глобальную природу, такие как:  
  
-   Состояния среды  
  
-   Текущих данных о диагностике уровня среды  
  
-   Дескрипторы подключений, выделенных в данный момент в среде  
  
-   Текущие значения каждого атрибута среды  
  
 В части кода, который реализует ODBC (диспетчера драйверов или драйвер) дескриптор среды определяет структуру, содержащую эту информацию.  
  
 Дескрипторы среды часто не используются в приложениях ODBC. Всегда используются в вызовах **SQLDataSources** и **SQLDrivers** и иногда используется в вызовах **SQLAllocHandle**, **SQLEndTran**, **SQLFreeHandle**, **SQLGetDiagField**, и **SQLGetDiagRec**.  
  
 Каждый фрагмент кода, который реализует ODBC (диспетчера драйверов или драйвер) содержит один или несколько дескрипторов среды. Например диспетчер драйверов хранит дескриптор отдельную среду для каждого приложения, подключенные к нему. Дескрипторы среды выделяются с **SQLAllocHandle** и освобождается с помощью **SQLFreeHandle**.
