---
title: SQLGetData (драйверы для настольных баз данных) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], Desktop Database Drivers
ms.assetid: c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae546182d51663c15a14ac25b5349a06da02e952
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (драйверы для настольных баз данных)
Эта функция может получать данные из любого столбца ли после него, а также независимо от порядка, в которой извлекаются столбцы существуют связанные столбцы.  
  
> [!NOTE]  
>  \*pcbValue в **SQLGetData** может вернуть два раза больше символов, как фактически доступного во время привязки к данным ANSI длиннее 510 символов в базе данных Jet 4.0. Значения символов или меньше 510 возвращает фактический cbValue.
