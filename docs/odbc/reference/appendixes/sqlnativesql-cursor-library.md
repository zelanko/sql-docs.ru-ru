---
description: SQLNativeSql (библиотека курсоров)
title: SQLNativeSql (библиотека курсоров) | Документация Майкрософт
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
ms.openlocfilehash: 6046c8dabbc128a3afae772730cbad9eacc4b61c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424912"
---
# <a name="sqlnativesql-cursor-library"></a>SQLNativeSql (библиотека курсоров)
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе обсуждается использование функции **SQLNativeSql** в библиотеке курсоров. Общие сведения о **SQLNativeSql**см. в разделе [функция SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md).  
  
 Если драйвер поддерживает эту функцию, Библиотека курсоров вызывает **SQLNativeSql** в драйвере и передает ей инструкцию SQL. Для позиционированного обновления, позиционированного удаления и **SELECT для инструкций UPDATE** библиотека курсоров изменяет инструкцию перед передачей ее драйверу.  
  
> [!NOTE]  
>  Библиотека курсоров неправильно возвращает значение SQLSTATE 34000 (недопустимое имя курсора), если имя курсора недопустимо в инструкции позиционированного обновления или удаления, передаваемой в аргументе *инстатементтекст* объекта **SQLNativeSql**. **SQLNativeSql** не предназначен для возврата синтаксических ошибок, которые возвращаются только при подготовке или выполнении инструкции.
