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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125601"
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 В этом разделе рассматривается использование **SQLRowCount** функции в библиотеку курсоров. Общие сведения о **SQLRowCount**, см. в разделе [функция SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md).  
  
 Если приложение вызывает **SQLRowCount** с оператором, связанный с курсором, библиотека курсоров возвращает количество строк данных, извлеченных из драйвера.  
  
 Если приложение вызывает **SQLRowCount** с оператором, связанных с позиционированного обновления или инструкции delete, библиотеку курсоров возвращает количество строк, затронутых при выполнении инструкции.  
  
 Если приложение вызывает **SQLRowCount** после **ВЫБЕРИТЕ** инструкция, библиотека курсоров возвращает -1.
