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
manager: craigg
ms.openlocfilehash: 43be1c5e75998903ff4e64fc5f4230818a873ffc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63281126"
---
# <a name="odbc-drivers-subkey"></a>Подраздел драйвера ODBC
Значения в подразделе драйверы ODBC список установленных драйверов. В следующей таблице показан формат из следующих значений.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|*Описание драйвера*|REG_SZ|**установлен**|  
  
 *Описание драйвера* имя определяется разработчиком драйвера. Обычно это имя СУБД, связанные с драйвером.  
  
 Например предположим, что будут установлены драйверы для файлов форматированного текста и SQL Server. Может принимать следующие значения в подразделе драйверы ODBC:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
