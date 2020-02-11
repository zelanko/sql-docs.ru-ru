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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 26e5c36b41f68627a634714cfa06525c99451450
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67947054"
---
# <a name="setup-dll-api-reference"></a>Справочник по API библиотеки DLL установки
В этом разделе описывается синтаксис API библиотеки DLL установки драйвера, который состоит из двух функций (**конфигдривер** и **ConfigDSN**). **Конфигдривер** и **ConfigDSN** могут быть либо в библиотеке DLL драйвера, либо в отдельной библиотеке DLL установки.  
  
 Кроме того, в этом разделе описывается синтаксис API-интерфейса установки транслятора, который состоит из одной функции (**конфигтранслатор**). **Конфигтранслатор** может быть либо в библиотеке DLL транслятора, либо в отдельной библиотеке DLL установки.  
  
 Каждая функция помечена версией ODBC, в которой она была представлена.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Функция ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [Функция ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [Функция ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)
