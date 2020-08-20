---
description: Подраздел ODBC-преобразователей
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
ms.openlocfilehash: 46308518f1f806cea21bbb824312d5269f8b61e4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499717"
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
