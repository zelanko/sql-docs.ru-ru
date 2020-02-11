---
title: Подраздел драйверов ODBC | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: eb54ba7becad42d8d9d2c2870c02db37a3c7d89f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093979"
---
# <a name="odbc-drivers-subkey"></a>Подраздел драйвера ODBC
Значения в подразделе драйверы ODBC имеют список установленных драйверов. Формат этих значений приведен в следующей таблице.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|*Описание драйвера*|REG_SZ|**Установка**|  
  
 Имя *описания драйвера* определяется разработчиком драйвера. Обычно это имя СУБД, связанной с драйвером.  
  
 Например, предположим, что драйверы установлены для форматированных текстовых файлов и SQL Server. Значения в подразделе драйверов ODBC могут быть такими:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
