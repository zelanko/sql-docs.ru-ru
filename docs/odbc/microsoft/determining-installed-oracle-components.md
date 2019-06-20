---
title: Определение установленных компонентов Oracle | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], determining installed components
ms.assetid: 3b018f6a-9db0-4aa1-8ec4-afc5f76d7cad
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7de783ae116a61aaa4c8801ca132127352020161
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63240281"
---
# <a name="determining-installed-oracle-components"></a>Определение установленных компонентов Oracle
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Чтобы определить компоненты Oracle, установленные в системе (и их версий), перейдите в каталог \Orainst Oracle в домашнем каталоге. Откройте один из следующих текстовых файлов: NT.rgs Win95.rgs и Win98.rgs.  
  
 Формат файла — аналогичен следующему:  
  
```  
0 ntinstall     all    "orainst"  "3.3.1.0.0C"  "Oracle Installer"  
20 w32tcp80     adp80  "tcp80"    "8.0.5.0.0"   "Oracle TCP/IP Pro"  
23 w32nmp80     adp80  "nmp80"    "8.0.5.0.0"   "Oracle Named Pipe"  
26 w32util80    all    "util80"   "8.0.5.0.0"   "Oracle8 Utilities"  
34 w32rsf80     all    "rsf80"    "8.0.5.0.0"   "Required Support"  
47 w32netclt80  net80  "netc80"   "8.0.5.0.0"   "Oracle Net8 Client"  
69 w32plus80    all    "plus80"   "8.0.5.0.0"   "SQL*Plus"  
```  
  
 Файлы .rgs также включать сведения об установке и описания каждого компонента.
