---
title: Настройка DLL API Ссылка (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: f9d03f17-1c0d-4e7c-9c04-8c316e07ef25
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 25cff50b73868b5b3015dfc1a00c560c344a6d36
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298889"
---
# <a name="setup-dll-api-reference"></a>Справочник по API библиотеки DLL установки
В этом разделе описывается синтаксис установки драйвера DLL API, которая состоит из двух функций **(ConfigDriver** и **ConfigDSN**). **ConfigDriver** и **ConfigDSN** могут быть либо в драйвере DLL, либо в отдельной установке DLL.  
  
 Кроме того, в этом разделе описывается синтаксис настройки переводчика DLL API, который состоит из одной функции **(ConfigTranslator**). **ConfigTranslator** может быть либо в переводчике DLL, либо в отдельной настройке DLL.  
  
 Каждая функция помечена версией ODBC, в которой она была введена.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Функция ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [Функция ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [Функция ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)
