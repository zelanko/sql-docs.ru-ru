---
title: SQLRowCount (библиотека курсоров) | Документы Microsoft
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
- SQLRowCount function [ODBC], Cursor Library
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 548387e46b4ce1d840c6bf0bb48112d45b643583
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLRowCount** функции в библиотеку курсоров. Общие сведения о **SQLRowCount**, в разделе [SQLRowCount, функция](../../../odbc/reference/syntax/sqlrowcount-function.md).  
  
 Если приложение вызывает **SQLRowCount** с оператором, связанный с курсором, библиотеку курсоров возвращает количество строк данных, извлеченных из драйвера.  
  
 Если приложение вызывает **SQLRowCount** с помощью инструкции, связанные с позиционированного обновления или инструкции delete, библиотеку курсоров возвращает количество строк, затронутых при выполнении инструкции.  
  
 Если приложение вызывает **SQLRowCount** после **ВЫБЕРИТЕ** инструкция, библиотеку курсоров возвращает – 1.
