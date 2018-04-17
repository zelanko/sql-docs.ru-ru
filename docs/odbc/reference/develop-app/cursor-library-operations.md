---
title: Операции с библиотекой курсоров | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], backward compatibility
- compatibility [ODBC], cursor library
- upgrading applications [ODBC], cursor library
- application upgrades [ODBC], cursor library
- backward compatibility [ODBC], cursor library
- cursor library [ODBC], backward compatibility
ms.assetid: 04d514b1-dc4d-4b84-bf35-60f4657ef1f6
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0bac09cb2b45274a5589c152a5b0e714b71f8dc1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="cursor-library-operations"></a>Операции с библиотекой курсоров
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 Если приложение, работа с ODBC 2*.x* драйвер выполняет вызовы ODBC 3. *x* библиотека курсоров, приложение может иметь возможность использовать ODBC 3. *x* функции, не поддерживаемые ODBC 2*.x* драйвера. Разработчик приложения следует соблюдать осторожность, способ использования этих функций, однако. Использование ODBC 3. *x* препятствовать библиотека курсоров ODBC 2*.x* драйвера в ODBC 3. *x* драйвера.
