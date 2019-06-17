---
title: SQLGetData (драйверы для настольных систем баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], Desktop Database Drivers
ms.assetid: c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6f362d725f8b734ab9ecdbdc79c268af08a495b4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63313141"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (драйверы для баз данных на настольном компьютере)
Эта функция может получать данные из любого столбца, ли после него и независимо от порядка, в которой извлекаются столбцы существуют привязанные столбцы.  
  
> [!NOTE]  
>  \*pcbValue в **SQLGetData** может вернуть два раза больше символов, как реально доступной при привязке к данным ANSI длиннее 510 символов в базе данных Jet 4.0. Значения символов до 510 человек возвращает фактический cbValue.
