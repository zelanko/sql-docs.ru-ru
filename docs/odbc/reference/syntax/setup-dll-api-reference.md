---
title: Справочник по API DLL установки | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298889"
---
# <a name="setup-dll-api-reference"></a>Справочник по API библиотеки DLL установки
В этом разделе описывается синтаксис API библиотеки DLL установки драйвера, который состоит из двух функций (**конфигдривер** и **ConfigDSN**). **Конфигдривер** и **ConfigDSN** могут быть либо в библиотеке DLL драйвера, либо в отдельной библиотеке DLL установки.  
  
 Кроме того, в этом разделе описывается синтаксис API-интерфейса установки транслятора, который состоит из одной функции (**конфигтранслатор**). **Конфигтранслатор** может быть либо в библиотеке DLL транслятора, либо в отдельной библиотеке DLL установки.  
  
 Каждая функция помечена версией ODBC, в которой она была представлена.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Функция ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [Функция ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [Функция ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)
