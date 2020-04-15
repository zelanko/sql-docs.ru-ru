---
title: S'LRowCount (Библиотека Курзора) Документы Майкрософт
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
ms.openlocfilehash: bf9fe597f54ecb4bc82439251e2228ac5fdc4ea3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300594"
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 На этой теме обсуждается использование функции **S'LRowCount** в библиотеке курсоров. Для получения общей информации о **S'LRowCount,** [см.](../../../odbc/reference/syntax/sqlrowcount-function.md)  
  
 Когда приложение вызывает **S'LRowCount** с помощью оператора, связанного с курсором, библиотека курсора возвращает количество строк данных, полученных от драйвера.  
  
 Когда приложение вызывает **S'LRowCount** с заявлением, связанным с позиционированным обновлением или удалением, библиотека курсора возвращает количество строк, затронутых утверждением.  
  
 Когда приложение вызывает **S'LRowCount** после оператора **SELECT,** библиотека курсоров возвращается -1.
