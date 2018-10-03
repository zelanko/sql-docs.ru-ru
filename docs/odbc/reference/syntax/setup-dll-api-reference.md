---
title: Справочник по API библиотеки DLL программы установки | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: d81bb9f5ec54f3d66089205f5b5941119d365501
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622212"
---
# <a name="setup-dll-api-reference"></a>Справочник по API библиотеки DLL установки
В этом разделе описывается синтаксис установки драйвера API библиотеки DLL, который состоит из двух функций (**ConfigDriver** и **ConfigDSN**). **ConfigDriver** и **ConfigDSN** можно в DLL-Библиотека драйвера или в отдельной библиотеки DLL программы установки.  
  
 Кроме того, в этом разделе описывается синтаксис установки translator API библиотеки DLL, который состоит из одной функции (**ConfigTranslator**). **ConfigTranslator** можно в translator DLL или в отдельной библиотеки DLL программы установки.  
  
 Каждая функция помечается используемая версия ODBC, в которую было включено.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Функция ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [Функция ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [Функция ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)
