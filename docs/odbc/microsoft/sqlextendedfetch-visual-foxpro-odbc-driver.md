---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2d01c25044bf7b03e2fabe9c615668fc7837312
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63313252"
---
# <a name="sqlextendedfetch-visual-foxpro-odbc-driver"></a>SQLExtendedFetch (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: Полное  
  
 Соответствие API ODBC: Уровень 2  
  
 Аналогичную [SQLFetch](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md) , но возвращает несколько строк с помощью массива для каждого столбца. Результирующий набор поддерживает прокрутку вперед и могут выполняться обратной прокручиваемые Если курсора определяется как статический, не последовательного доступа.  
  
 По умолчанию драйвер ODBC для Visual FoxPro не возвращает строк, помечаются как удаленные в таблице FoxPro. Строки помечаются для удаления, но еще не удаленных из таблицы не включаются в курсор результирующего набора. Это поведение можно изменить с помощью [SET DELETED](../../odbc/microsoft/set-deleted-command.md) команды.  
  
 Дополнительные сведения см. в разделе [SQLExtendedFetch](../../odbc/reference/syntax/sqlextendedfetch-function.md) в *Справочник по программированию ODBC*.
