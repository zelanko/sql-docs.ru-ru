---
description: Статус строки
title: Состояние строки | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- row status [ODBC]
- cache [ODBC]
ms.assetid: 0f0b1fb6-f697-4ced-811c-2908e210bc71
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8970e78d523ca86a50edb1e27b159ef15a1a1747
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424966"
---
# <a name="row-status"></a>Статус строки
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Библиотека курсоров создает буфер в кэше для состояния строки. Библиотека курсоров извлекает значения для массива состояния строки (указанного в атрибуте оператора SQL_ATTR_ROW_STATUS_PTR) из этого буфера. Для каждой строки библиотека курсоров задает для этого буфера следующие сведения:  
  
-   SQL_ROW_DELETED при выполнении инструкции позиционированного удаления в строке.  
  
-   SQL_ROW_ERROR при возникновении ошибки при получении строки из источника данных с помощью **SQLFetch**.  
  
-   SQL_ROW_SUCCESS, когда она успешно извлекает строку из источника данных с помощью **SQLFetch**.  
  
-   SQL_ROW_UPDATED при выполнении инструкции позиционированного обновления в строке.
