---
title: Типы драйверов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
ms.assetid: 864c53c1-b68a-48b6-b6bc-5ecb520bb9dc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: de6d8e1473f127d28c69969e0fc298afd69d3023
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304875"
---
# <a name="types-of-drivers"></a>Типы драйверов
Драйверы ODBC можно классифицировать следующим образом:  
  
-   **32-разрядный ODBC 2.**  
     **драйвер _x_ ** 32-разрядный драйвер:  
  
    -   Экспортирует только функции ODBC *2. x* .  
  
    -   Поведение ODBC *2. x* при изменении поведения.  
  
-   **ISO и Open Group-совместимый драйвер** 32-разрядный драйвер, который:  
  
    -   Экспортирует все функции, описанные в документах Open Group или ISO CLI. К ним относятся некоторые функции, которые не рекомендуются в ODBC.  
  
    -   Поведение ODBC 3,0 при изменении поведения.  
  
    -   Не обязательно пройти через диспетчер драйверов ODBC 3,0.  
  
-   **Драйвер ODBC 3,0** 32-разрядный драйвер, который:  
  
    -   Экспортирует только функции, которые находятся в ODBC 3,0 минус устаревшие функции.  
  
    -   Может работать с поведением ODBC *2. x* или поведением ODBC 3,0 в отношении изменений поведения, основанных на атрибуте среды SQL_ATTR_APP_ODBC_VERSION.  
  
-   **Драйвер ODBC 3,5 (или более поздней версии) для ANSI** 32-разрядный драйвер, который:  
  
    -   Экспортирует только функции, которые находятся в ODBC 3,5 минус устаревшие функции.  
  
    -   Может работать с поведением ODBC *2. x* или поведением ODBC 3,0 или поведением ODBC 3,5 в отношении изменений поведения, основанных на атрибуте среды SQL_ATTR_APP_ODBC_VERSION.  
  
-   **Драйвер для ODBC 3,5 (или более поздней версии)** 32-разрядный драйвер, который:  
  
    -   Поддерживает все функции драйвера ODBC 3,5 ANSI.  
  
    -   Экспортирует версии Юникода для всех строковых API ODBC.  
  
    -   Может хранить и обрабатывать данные в Юникоде в источнике данных.  
  
> [!NOTE]  
>  16-разрядные драйверы ODBC не будут работать непосредственно с диспетчером драйверов ODBC *3. x* . Однако 16-разрядные драйверы могут работать с диспетчером драйверов ODBC 2,0, который, в свою очередь, преобразовательет в диспетчер драйверов *3. x* .
