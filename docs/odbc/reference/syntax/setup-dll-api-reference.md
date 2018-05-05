---
title: Справочник по API библиотеки DLL по установке | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: f9d03f17-1c0d-4e7c-9c04-8c316e07ef25
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0c8ef5d12cbe85bf4a575fe0b7d8d2687e12b1b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setup-dll-api-reference"></a>Справочник по API библиотеки DLL программы установки
В этом разделе описывается синтаксис установки драйвера API библиотеки DLL, который состоит из двух функций (**ConfigDriver** и **ConfigDSN**). **ConfigDriver** и **ConfigDSN** можно в DLL-Библиотека драйвера или в отдельном установки библиотеки DLL.  
  
 Кроме того, в этом разделе описывается синтаксис установки переводчик API библиотеки DLL, который состоит из одной функции (**ConfigTranslator**). **ConfigTranslator** можно в преобразователь DLL или в отдельном установки библиотеки DLL.  
  
 Каждая функция помечается используемая версия ODBC, в которой он был представлен.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Функция ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [Функция ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [Функция ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)
