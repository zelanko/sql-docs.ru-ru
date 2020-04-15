---
title: SQLCloseCursor_ODBC Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e1b61267d093e11bf7ea25158f5dc6a29ccba6a1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296304"
---
# <a name="sqlclosecursor_odbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 На этой теме обсуждается вопрос об использовании функции **S'LCloseCursor** в библиотеке курсоров. Для получения общей информации о **s'LCloseCursor,** [см.](../../../odbc/reference/syntax/sqlclosecursor-function.md)  
  
 Библиотека курсоров не поддерживает вызов **S'LCloseCursor** без открытого курсора. Попытка этого вернет S'LSTATE 24000 (состояние недействительного курсора). Вызов **S'LFreeStmt** с *опцией* SQL_CLOSE, когда курсор не открыт, поддерживается библиотекой курсора.
