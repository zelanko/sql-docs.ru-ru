---
title: "SQLCloseCursor_ODBC | Документы Microsoft"
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
- SQLCloseCursor function [ODBC], ODBC
ms.assetid: 5e47e3f7-e1b8-451f-bf75-daa19b7c7271
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fcc680ec815afa700c00c9d8a69c5826944153a4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlclosecursorodbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLCloseCursor** функции в библиотеку курсоров. Общие сведения о **SQLCloseCursor**, в разделе [функция SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md).  
  
 Библиотека курсоров не поддерживает вызов **SQLCloseCursor** без открытого курсора. Пытаться это вернет SQLSTATE 24000 (недопустимое состояние курсора). Вызов **SQLFreeStmt** с *параметр* из SQL_CLOSE при никакой курсор открыт поддерживается библиотекой курсоров.
