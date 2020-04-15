---
title: СЗЛНатиЯНатияКл (Библиотека Курзора) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLNativeSql function [ODBC], Cursor Library
ms.assetid: c4459092-1177-4b2a-b7f5-e0083d3bf2b2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 41f7617530f34d49852ca67db9f47cab94292385
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300574"
---
# <a name="sqlnativesql-cursor-library"></a>SQLNativeSql (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 На этой теме обсуждается использование функции **S'LNativeSql** в библиотеке курсоров. Для получения общей информации о **S'LNativeSl,** [см.](../../../odbc/reference/syntax/sqlnativesql-function.md)  
  
 Если драйвер поддерживает эту функцию, библиотека курсора вызывает **s'LNativeSl** в драйвере и передает ее в выписку s'L. Для позиционированного обновления, позиционирования удалить и **SELECT ДЛЯ ОБНОВЛЕНИЕ** заявления, библиотека курсора изменяет заявление, прежде чем передать его водителю.  
  
> [!NOTE]  
>  Библиотека курсоров неправильно возвращает S'LSTATE 34000 (имя недействительного курсора), если имя курсора является недействительным в позиционированном обновлении или удалении оператора, которое передается в аргументе *InStatementText* **s'LNativeSl.** **SLNativeSql** не предназначен для возврата ошибок синтаксиса, которые возвращаются только при подготовке или выполнении оператора.
