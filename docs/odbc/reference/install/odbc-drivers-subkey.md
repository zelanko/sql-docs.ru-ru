---
title: Подраздел драйвера ODBC | Документация Майкрософт
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093979"
---
# <a name="odbc-drivers-subkey"></a>Подраздел драйвера ODBC
Значения в подразделе драйверы ODBC список установленных драйверов. В следующей таблице показан формат из следующих значений.  
  
|Name|Тип данных|Data|  
|----------|---------------|----------|  
|*Описание драйвера*|REG_SZ|**установлен**|  
  
 *Описание драйвера* имя определяется разработчиком драйвера. Обычно это имя СУБД, связанные с драйвером.  
  
 Например предположим, что будут установлены драйверы для файлов форматированного текста и SQL Server. Может принимать следующие значения в подразделе драйверы ODBC:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
