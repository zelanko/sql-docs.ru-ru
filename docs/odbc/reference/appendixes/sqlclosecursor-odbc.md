---
title: SQLCloseCursor_ODBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLCloseCursor function [ODBC], ODBC
ms.assetid: 5e47e3f7-e1b8-451f-bf75-daa19b7c7271
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6477530573cc6fccd173e1cb1fbed7c59141a4e0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlclosecursorodbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLCloseCursor** функции в библиотеку курсоров. Общие сведения о **SQLCloseCursor**, в разделе [функция SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md).  
  
 Библиотека курсоров не поддерживает вызов **SQLCloseCursor** без открытого курсора. Пытаться это вернет SQLSTATE 24000 (недопустимое состояние курсора). Вызов **SQLFreeStmt** с *параметр* из SQL_CLOSE при никакой курсор открыт поддерживается библиотекой курсоров.
