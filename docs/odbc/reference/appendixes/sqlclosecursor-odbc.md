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
ms.topic: article
helpviewer_keywords:
- SQLCloseCursor function [ODBC], ODBC
ms.assetid: 5e47e3f7-e1b8-451f-bf75-daa19b7c7271
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d9df09aea21ed6a1e7768dfd04ab283a8342d355
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlclosecursorodbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLCloseCursor** функции в библиотеку курсоров. Общие сведения о **SQLCloseCursor**, в разделе [функция SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md).  
  
 Библиотека курсоров не поддерживает вызов **SQLCloseCursor** без открытого курсора. Пытаться это вернет SQLSTATE 24000 (недопустимое состояние курсора). Вызов **SQLFreeStmt** с *параметр* из SQL_CLOSE при никакой курсор открыт поддерживается библиотекой курсоров.
