---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0cb17ed043a6b533b007769b9cbb28652d06e6f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47719618"
---
# <a name="sqltransact-access-driver"></a>SQLTransact (драйвер для Access)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера доступа. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Если используется драйвер Microsoft Access, параметром SQL_COMMIT и SQL_ROLLBACK поддерживаются для *fType* аргумента в вызове **SQLTransact**.  
  
 Если происходит сбой в процессе фиксации, затронутые базы данных могут быть восстановлены с помощью параметра восстановления базы данных, в программе установки драйвера Microsoft Access или при помощи ключевого слова REPAIR_DB в **SQLConfigDataSource** функция.
