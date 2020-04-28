---
title: Подраздел "трансляторы ODBC" | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296224"
---
# <a name="odbc-translators-subkey"></a>Подраздел ODBC-преобразователей
В подразделе "трансляторы ODBC" перечислены установленные переводчики. Формат этих значений приведен в следующей таблице.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|*Переводчик — DESC*|REG_SZ|**Установлено**|  
  
 Имя *переводчика-DESC* определяется разработчиком переводчика.  
  
 Например, предположим, что пользователь установил преобразователь кодовых страниц Microsoft® и пользовательский код ASCII в переводчике EBCDIC. Значения в подразделе "трансляторы ODBC" могут выглядеть следующим образом:  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
