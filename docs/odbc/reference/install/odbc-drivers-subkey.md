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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dd1f8d3293e35a543cce6b5079d9c6e10a331a88
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304035"
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
