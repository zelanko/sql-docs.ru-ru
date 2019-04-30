---
title: SQLCloseCursor_ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLCloseCursor function [ODBC], ODBC
ms.assetid: 5e47e3f7-e1b8-451f-bf75-daa19b7c7271
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 827f7195c5d4eb4f67cb3298b75519a5583053d1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199503"
---
# <a name="sqlclosecursorodbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 В этом разделе рассматривается использование **SQLCloseCursor** функции в библиотеку курсоров. Общие сведения о **SQLCloseCursor**, см. в разделе [функция SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md).  
  
 Библиотека курсоров поддерживает вызов метода **SQLCloseCursor** без открытого курсора. Тут вернет SQLSTATE 24000 (недопустимое состояние курсора). Вызов **SQLFreeStmt** с *параметр* из SQL_CLOSE когда открыт без курсора поддерживается библиотекой курсоров.
