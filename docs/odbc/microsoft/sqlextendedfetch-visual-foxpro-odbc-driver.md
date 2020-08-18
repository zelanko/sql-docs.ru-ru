---
description: SQLExtendedFetch (драйвер ODBC для Visual FoxPro)
title: SQLExtendedFetch (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b28af112-fb47-4143-b11e-3b743b2ae1b8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7f938dda4e9e474854d62c50401ee0bf91317983
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449176"
---
# <a name="sqlextendedfetch-visual-foxpro-odbc-driver"></a>SQLExtendedFetch (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полная  
  
 Соответствие API-интерфейса ODBC: уровень 2  
  
 Аналогично [SQLFetch](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md) , но возвращает несколько строк с помощью массива для каждого столбца. Результирующий набор доступен для прокрутки и может быть выполнен с возможностью обратной прокрутки, если курсор определен как статический, а не однонаправленный.  
  
 По умолчанию драйвер ODBC для Visual FoxPro не возвращает строки, помеченные как удаленные, в таблице FoxPro. Строки, помеченные для удаления, но еще не удаленные из таблицы, не включаются в курсор результирующего набора. Это поведение можно изменить с помощью команды [SET DELETED](../../odbc/microsoft/set-deleted-command.md) .  
  
 Дополнительные сведения см. в разделе [SQLExtendedFetch](../../odbc/reference/syntax/sqlextendedfetch-function.md) в *справочнике программиста по ODBC*.
