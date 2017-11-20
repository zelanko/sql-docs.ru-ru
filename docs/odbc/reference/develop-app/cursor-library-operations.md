---
title: "Операции с библиотекой курсоров | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
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
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 00469dcf77ae81f5d02765026fe0c1f7194da5d1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="cursor-library-operations"></a>Операции с библиотекой курсоров
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 Если приложение, работа с ODBC 2*.x* драйвер выполняет вызовы ODBC 3. *x* библиотека курсоров, приложение может иметь возможность использовать ODBC 3. *x* функции, не поддерживаемые ODBC 2*.x* драйвера. Разработчик приложения следует соблюдать осторожность, способ использования этих функций, однако. Использование ODBC 3. *x* препятствовать библиотека курсоров ODBC 2*.x* драйвера в ODBC 3. *x* драйвера.

