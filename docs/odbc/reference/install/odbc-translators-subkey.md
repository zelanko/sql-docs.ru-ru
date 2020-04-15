---
title: Подключка переводчиков ODBC (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 617416adfcddfbf041c48acbf83cb9589e34ae27
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296224"
---
# <a name="odbc-translators-subkey"></a>Подраздел ODBC-преобразователей
Значения в подключке ODBC Translators перечисляют установленные переводчики. Формат этих значений отображается в следующей таблице.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|*переводчик-деск*|REG_SZ|**Установлены**|  
  
 Имя *переводчика-desc* определяется разработчиком переводчика.  
  
 Например, предположим, что пользователь установил на переводчик eBCDIC ® страницу кода microsoft® и пользовательский ASCII. Значения в подключке ПЕРЕВОДЧИКов ODBC могут быть следующими:  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
