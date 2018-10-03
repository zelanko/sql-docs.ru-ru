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
manager: craigg
ms.openlocfilehash: 2125d299570c3e5b381a6bfa5500b5b5e61636f0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47772032"
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 В этом разделе рассматривается использование **SQLRowCount** функции в библиотеку курсоров. Общие сведения о **SQLRowCount**, см. в разделе [функция SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md).  
  
 Если приложение вызывает **SQLRowCount** с оператором, связанный с курсором, библиотека курсоров возвращает количество строк данных, извлеченных из драйвера.  
  
 Если приложение вызывает **SQLRowCount** с оператором, связанных с позиционированного обновления или инструкции delete, библиотеку курсоров возвращает количество строк, затронутых при выполнении инструкции.  
  
 Если приложение вызывает **SQLRowCount** после **ВЫБЕРИТЕ** инструкция, библиотека курсоров возвращает – 1.
