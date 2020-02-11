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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 086c5381f1801baf919508525c17faab93746ca0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68003359"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (драйверы для баз данных на настольном компьютере)
Эта функция может извлекать данные из любого столбца, независимо от того, имеются ли связанные столбцы после этого и вне зависимости от порядка, в котором извлекаются столбцы.  
  
> [!NOTE]  
>  \*Пкбвалуе в **SQLGetData** может возвращать вдвое столько символов, сколько действительно доступно при привязке к данным в формате ANSI длиннее 510 символов в базе данных Jet 4,0. Символьные значения 510 или меньше будут возвращать фактический Кбвалуе.
