---
title: SQLNativeSql (библиотека курсоров) | Документы Microsoft
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
- SQLNativeSql function [ODBC], Cursor Library
ms.assetid: c4459092-1177-4b2a-b7f5-e0083d3bf2b2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f9ce0357981dbc7a499bf0dc0cefc52313a2596a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlnativesql-cursor-library"></a>SQLNativeSql (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLNativeSql** функции в библиотеку курсоров. Общие сведения о **SQLNativeSql**, в разделе [функция SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md).  
  
 Если драйвер поддерживает эту функцию, вызывает библиотеку курсоров **SQLNativeSql** в драйвере и передает его в инструкцию SQL. Позиционированные обновления располагается delete, и **ВЫБЕРИТЕ для обновления** инструкций, библиотеку курсоров изменяет инструкцию перед его передачей в драйвере.  
  
> [!NOTE]  
>  Библиотека курсоров неправильно возвращает SQLSTATE 34000 (недопустимое имя курсора), если имя курсора является недопустимым в позиционированного обновления или инструкции delete, который передается в *InStatementText* аргумент **SQLNativeSql** . **SQLNativeSql** не предназначен для возврата синтаксических ошибок, которые возвращаются только при подготовке инструкции или выполнения.
