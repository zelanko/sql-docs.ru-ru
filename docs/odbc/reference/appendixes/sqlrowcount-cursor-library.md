---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: be902866cfcf98a10af2c3741926de8b7541bb79
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125601"
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLRowCount** в библиотеке курсоров. Общие сведения о **SQLRowCount**см. в разделе [функция SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md).  
  
 Когда приложение вызывает **SQLRowCount** с инструкцией, связанной с курсором, Библиотека курсоров возвращает число строк данных, извлеченных из драйвера.  
  
 Когда приложение вызывает **SQLRowCount** с инструкцией, связанной с позиционированным обновлением или инструкцией DELETE, Библиотека курсоров возвращает число строк, затронутых инструкцией.  
  
 Когда приложение вызывает **SQLRowCount** после инструкции **SELECT** , Библиотека курсоров возвращает значение-1.
