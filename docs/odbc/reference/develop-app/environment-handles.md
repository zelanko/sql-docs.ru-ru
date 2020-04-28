---
title: Дескрипторы окружения | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b504995e99dfad032598485e370b4d5a6681ae81
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300444"
---
# <a name="environment-handles"></a>Дескрипторы среды
*Среда* — это глобальный контекст для доступа к данным; связанный с средой — любая глобальная информация по природе, например:  
  
-   Состояние среды  
  
-   Текущая диагностика на уровне среды  
  
-   Дескрипторы подключений, выделенных в настоящий момент в окружении  
  
-   Текущие параметры для каждого атрибута среды  
  
 В фрагменте кода, который реализует ODBC (диспетчер драйверов или драйвер), обработчик среды определяет структуру, содержащую эти сведения.  
  
 Дескрипторы среды часто не используются в приложениях ODBC. Они всегда используются в вызовах **SQLDataSources** и **SQLDrivers** и иногда используются в вызовах **функцию SQLAllocHandle**, **SQLEndTran**, **SQLFreeHandle**, **SQLGetDiagField**и **SQLGetDiagRec**.  
  
 Каждый фрагмент кода, который реализует ODBC (диспетчер драйверов или драйвер), содержит один или несколько дескрипторов среды. Например, диспетчер драйверов поддерживает отдельный обработчик среды для каждого подключенного к нему приложения. Дескрипторы среды выделяются с помощью **функцию SQLAllocHandle** и освобождаются с помощью **SQLFreeHandle**.
