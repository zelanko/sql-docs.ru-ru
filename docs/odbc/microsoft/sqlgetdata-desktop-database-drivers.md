---
title: SQLGetData (драйверы баз данных для настольных систем) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2b102d8435831d45aad3c2049581513e0493de9a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304125"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (драйверы для баз данных на настольном компьютере)
Эта функция может извлекать данные из любого столбца, независимо от того, имеются ли связанные столбцы после этого и вне зависимости от порядка, в котором извлекаются столбцы.  
  
> [!NOTE]  
>  \*Пкбвалуе в **SQLGetData** может возвращать вдвое столько символов, сколько действительно доступно при привязке к данным в формате ANSI длиннее 510 символов в базе данных Jet 4,0. Символьные значения 510 или меньше будут возвращать фактический Кбвалуе.
