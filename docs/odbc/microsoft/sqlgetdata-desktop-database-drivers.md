---
title: "SQLGetData (драйверы для настольных баз данных) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLGetData function [ODBC], Desktop Database Drivers
ms.assetid: c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e091bf31e034eaabb9c87931bc6b128f5bdeba84
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (драйверы для настольных баз данных)
Эта функция может получать данные из любого столбца ли после него, а также независимо от порядка, в которой извлекаются столбцы существуют связанные столбцы.  
  
> [!NOTE]  
>  \*pcbValue в **SQLGetData** может вернуть два раза больше символов, как фактически доступного во время привязки к данным ANSI длиннее 510 символов в базе данных Jet 4.0. Значения символов или меньше 510 возвращает фактический cbValue.

