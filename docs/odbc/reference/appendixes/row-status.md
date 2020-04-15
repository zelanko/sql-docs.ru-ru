---
title: Статус строки Документы Майкрософт
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
ms.openlocfilehash: d4ae4169dc3f2a491663f4a86c564cfee5c2f4d6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305103"
---
# <a name="row-status"></a>Статус строки
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Библиотека курсора создает буфер в кэше для состояния строки. Библиотека курсора извлекает из этого буфера значения для массива состояния строки (указано с SQL_ATTR_ROW_STATUS_PTR атрибутом оператора). Для каждой строки библиотека курсора устанавливает этот буфер для:  
  
-   SQL_ROW_DELETED при выполнении оператора удаления на строке.  
  
-   SQL_ROW_ERROR, когда он сталкивается с ошибкой, извлекающей строку из источника данных с **помощью S'LFetch.**  
  
-   SQL_ROW_SUCCESS, когда он успешно извлекает строку из источника данных с **помощью S'LFetch.**  
  
-   SQL_ROW_UPDATED при выполнении оператора обновления на строке.
