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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7d26f2d33d81e08cfe4bddff9b2260bd2f098f00
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093945"
---
# <a name="odbc-translators-subkey"></a>Подраздел ODBC-преобразователей
В подразделе "трансляторы ODBC" перечислены установленные переводчики. Формат этих значений приведен в следующей таблице.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|*Переводчик — DESC*|REG_SZ|**Установка**|  
  
 Имя *переводчика-DESC* определяется разработчиком переводчика.  
  
 Например, предположим, что пользователь установил преобразователь кодовых страниц Microsoft® и пользовательский код ASCII в переводчике EBCDIC. Значения в подразделе "трансляторы ODBC" могут выглядеть следующим образом:  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
