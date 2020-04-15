---
title: Подключи спецификации переводчика Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator subkey [ODBC]
- registry entries for components [ODBC], translator specification subkeys
- translator specification subkeys [ODBC]
- subkeys [ODBC], translator specification subkeys
ms.assetid: 3c0edeee-d43a-4466-a177-bf2d2435707a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ad21943c5313edcb09aba88d45ea21132aa9757f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296044"
---
# <a name="translator-specification-subkeys"></a>Подразделы спецификаций преобразователей
Каждый переводчик, указанный в подключке ПЕРЕВОДЧИКов ODBC, имеет свой собственный подключ. Этот подключ имеет то же имя, что и соответствующее значение под подключку ODBC Translators. Значения в этом подключке перечисляют полные пути настройки DLL переводчика и переводчика и количество использования. Форматы значений показаны в следующей таблице.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|API перевода|REG_SZ|*переводчик-DLL-путь*|  
|Настройка|REG_SZ|*установка-DLL-путь*|  
|UsageCount|REG_DWORD|*count*|  
  
 Для получения информации о подсчете использования смотрите [подсчет использования](../../../odbc/reference/install/usage-counting.md) ранее в этом разделе.  
  
 Приложения не должны устанавливать количество использования. ODBC будет поддерживать этот счет.  
  
 Например, предположим, что переводчик страницы кода Майкрософт имеет перевод DLL под названием Mscpxl32.dll, что функции настройки переводчика находятся в одном И том же DLL и что переводчик был установлен три раза. Значения в подключке Microsoft Code Page Translator могут быть следующими:  
  
```  
Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
UsageCount : REG_DWORD : 0x3  
```
