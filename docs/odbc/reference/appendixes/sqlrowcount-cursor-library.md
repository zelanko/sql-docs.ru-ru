---
title: "SQLRowCount (библиотека курсоров) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLRowCount function [ODBC], Cursor Library
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9460f4f4bbc522fc421b7e40b261fe17a8410a09
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLRowCount** функции в библиотеку курсоров. Общие сведения о **SQLRowCount**, в разделе [SQLRowCount, функция](../../../odbc/reference/syntax/sqlrowcount-function.md).  
  
 Если приложение вызывает **SQLRowCount** с оператором, связанный с курсором, библиотеку курсоров возвращает количество строк данных, извлеченных из драйвера.  
  
 Если приложение вызывает **SQLRowCount** с помощью инструкции, связанные с позиционированного обновления или инструкции delete, библиотеку курсоров возвращает количество строк, затронутых при выполнении инструкции.  
  
 Если приложение вызывает **SQLRowCount** после **ВЫБЕРИТЕ** инструкция, библиотеку курсоров возвращает – 1.

