---
title: S'LGetData (Драйверы базы данных для рабочей стола) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304125"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (драйверы для баз данных на настольном компьютере)
Эта функция может получать данные из любого столбца, независимо от того, есть ли после него связанные столбцы и независимо от порядка, в котором извлекаются столбцы.  
  
> [!NOTE]  
>  \*pcbValue в **S'LGetData** может вернуть в два раза больше символов, чем фактически доступны при привязке к данным ANSI длиннее 510 символов в базе данных Jet 4.0. Значения символов 510 или менее вернут фактическое cbValue.
