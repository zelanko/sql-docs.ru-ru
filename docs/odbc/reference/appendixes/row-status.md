---
title: Строка состояния | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a62bad0e69a8bf8b5365575f97e4791cbbf270d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057109"
---
# <a name="row-status"></a>Статус строки
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 Библиотека курсоров создает буфер в кэше для строки состояния. Библиотека курсоров извлекает значения для состояния массив строк (указанный атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR) в данном буфере. Для каждой строки библиотека курсоров устанавливает этот буфер.  
  
-   Значение SQL_ROW_DELETED, при выполнении позиционированного удалить оператором в строке.  
  
-   SQL_ROW_ERROR при обнаружении ошибки при получении строки из источника данных с помощью **SQLFetch**.  
  
-   SQL_ROW_SUCCESS при успешно выборке строки из источника данных с помощью **SQLFetch**.  
  
-   SQL_ROW_UPDATED при выполнении инструкции позиционированного обновления в строке.
