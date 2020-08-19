---
description: SQLRowCount (библиотека курсоров)
title: SQLRowCount (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLRowCount function [ODBC], Cursor Library
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 02c972d4847ef0736e6f9e9ac91f8f617e1d9df0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424885"
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLRowCount** в библиотеке курсоров. Общие сведения о **SQLRowCount**см. в разделе [функция SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md).  
  
 Когда приложение вызывает **SQLRowCount** с инструкцией, связанной с курсором, Библиотека курсоров возвращает число строк данных, извлеченных из драйвера.  
  
 Когда приложение вызывает **SQLRowCount** с инструкцией, связанной с позиционированным обновлением или инструкцией DELETE, Библиотека курсоров возвращает число строк, затронутых инструкцией.  
  
 Когда приложение вызывает **SQLRowCount** после инструкции **SELECT** , Библиотека курсоров возвращает значение-1.
