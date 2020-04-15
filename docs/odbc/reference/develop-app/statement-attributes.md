---
title: Атрибуты заявления Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], statement attributes
- statement attributes [ODBC]
ms.assetid: 4c59cd8e-a713-4095-9065-20d5bdeafe43
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec24cc43e8c57e47ddda9f20fac1807f42453e84
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299647"
---
# <a name="statement-attributes"></a>Атрибуты инструкции
Атрибуты оператора являются характеристиками оператора. Например, следует ли использовать закладки и какой курсор использовать с набором результатов оператора являются атрибутами оператора.  
  
 Атрибуты оператора устанавливаются с **помощью S'LSetStmtAttr** и их текущих настроек, извлеченных с **помощью S'LGetStmtAttr.** Нет требования, чтобы приложение устанавливал какие-либо атрибуты оператора; все атрибуты оператора имеют значения по умолчанию, некоторые из которых специфичны для драйверов.  
  
 Когда атрибут оператора может быть установлен, зависит от самого атрибута. Атрибуты SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR и SQL_ATTR_USE_BOOKMARKS оператора должны быть установлены до выполнения оператора. Атрибуты SQL_ATTR_ASYNC_ENABLE и SQL_ATTR_NOSCAN оператора могут быть установлены в любое время, но не применяются до тех пор, пока заявление не будет использовано снова. SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS и SQL_ATTR_QUERY_TIMEOUT атрибуты оператора могут быть установлены в любое время, но это конкретные драйверы ли они применяются до того, как заявление будет использовано снова. Остальные атрибуты оператора могут быть установлены в любое время.  
  
> [!NOTE]  
>  Возможность установки атрибутов оператора на уровне соединения, позвонив в **ODBC** 3, была универсена. *x*. ODBC 3. *приложения x* никогда не должны устанавливать атрибуты оператора на уровне соединения. ODBC 3. *x* драйверам нужна только эта функциональность, если они должны работать с ODBC 2. *x* приложений. Для получения более подробной информации в приложении G: Руководство по обратной совместимости с [системой S'LSetConnectOption можно ознакомиться с информацией о s'LSetConnectOption.](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)  
>   
>  Исключением из этого являются SQL_ATTR_METADATA_ID и SQL_ATTR_ASYNC_ENABLE атрибуты, которые являются атрибутами соединения и атрибутами оператора и могут быть установлены либо на уровне соединения, либо на уровне оператора.  
>   
>  Ни один из атрибутов оператора, введенных в ODBC 3. *x* (за исключением SQL_ATTR_METADATA_ID) можно установить на уровне соединения.  
  
 Для получения более подробной информации ознакомьтесь с описанием функции [S'LSetStmtAttr.](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)
