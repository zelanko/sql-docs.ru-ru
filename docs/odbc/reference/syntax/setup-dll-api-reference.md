---
description: Справочник по API библиотеки DLL установки
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
ms.openlocfilehash: 5cb3e20a1c25d206a1dd27367bbe4a128af0818f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487337"
---
# <a name="setup-dll-api-reference"></a>Справочник по API библиотеки DLL установки
В этом разделе описывается синтаксис API библиотеки DLL установки драйвера, который состоит из двух функций (**конфигдривер** и **ConfigDSN**). **Конфигдривер** и **ConfigDSN** могут быть либо в библиотеке DLL драйвера, либо в отдельной библиотеке DLL установки.  
  
 Кроме того, в этом разделе описывается синтаксис API-интерфейса установки транслятора, который состоит из одной функции (**конфигтранслатор**). **Конфигтранслатор** может быть либо в библиотеке DLL транслятора, либо в отдельной библиотеке DLL установки.  
  
 Каждая функция помечена версией ODBC, в которой она была представлена.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Функция ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [Функция ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [Функция ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)
