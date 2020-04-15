---
title: Подключка драйверов ODBC (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dd1f8d3293e35a543cce6b5079d9c6e10a331a88
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304035"
---
# <a name="odbc-drivers-subkey"></a>Подраздел драйвера ODBC
Значения подключки ODBC Drivers перечисляют установленные драйверы. Формат этих значений отображается в следующей таблице.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|*водитель-описание*|REG_SZ|**Установлены**|  
  
 Имя *водителя-описания* определяется разработчиком драйвера. Обычно это имя DBMS, связанное с драйвером.  
  
 Например, предположим, что драйверы были установлены для отформатированных текстовых файлов и сервера S'L. Значения подключки ДРАЙВЕРов ODBC могут быть:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
