---
description: SQLTransact (драйвер для Access)
title: SQLTransact (драйвер для Access) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLTransact
- SQLTransact function [ODBC], Access Driver
ms.assetid: 892b79c7-9e20-4d1f-bc60-d4b25694ca25
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7e9b00f8f5a12af2d3823171d22ad53106569352
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339703"
---
# <a name="sqltransact-access-driver"></a>SQLTransact (драйвер для Access)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 При использовании драйвера Microsoft Access SQL_COMMIT и SQL_ROLLBACK поддерживаются аргументом *fType* в вызове **SQLTransact**.  
  
 В случае сбоя в процессе фиксации затронутая база данных может быть исправлена с помощью параметра восстановления базы данных в программе установки драйвера Microsoft Access или с помощью ключевого слова REPAIR_DB в функции **SQLConfigDataSource** .
