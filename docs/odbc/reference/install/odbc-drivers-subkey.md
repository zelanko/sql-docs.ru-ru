---
description: Подраздел драйвера ODBC
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b950a352c3da69a2a8de9a89f7bbebf87e0a597a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448924"
---
# <a name="odbc-drivers-subkey"></a>Подраздел драйвера ODBC
Значения в подразделе драйверы ODBC имеют список установленных драйверов. Формат этих значений приведен в следующей таблице.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|*Описание драйвера*|REG_SZ|**Установлено**|  
  
 Имя *описания драйвера* определяется разработчиком драйвера. Обычно это имя СУБД, связанной с драйвером.  
  
 Например, предположим, что драйверы установлены для форматированных текстовых файлов и SQL Server. Значения в подразделе драйверов ODBC могут быть такими:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
