---
title: СЗЛГетХАТС (Библиотека Курзора) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetFunctions function [ODBC], Cursor Library
ms.assetid: 931acd12-4eb6-4a78-9a77-157a18a9a2d0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f993a08aae1656b8d373911299e75852de855419
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307825"
---
# <a name="sqlgetfunctions-cursor-library"></a>SQLGetFunctions (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 На этой теме обсуждается использование функции **S'LGetFunctions** в библиотеке курсоров. Для получения общей информации о **функциях S'LGetFunctions**см. [SQLGetFunctions Function](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
 При вызове **S'LGetFunctions**, библиотека курсоров возвращает, что она поддерживает **S'LExtendedFetch**, **S'LFetchScroll**, **S'LSetPos**, и **S'LSetScrollOptions**, в дополнение к функциям, поддерживаемым драйвером.
