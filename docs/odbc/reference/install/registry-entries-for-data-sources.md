---
title: Записи реестра для источников данных | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC]
- data sources [ODBC], registry entries
- registry entries for data sources [ODBC], about registry entries
- data sources [ODBC], configuring
- registry entries for data sources [ODBC]
ms.assetid: 78aaa3d3-d081-4550-80e3-720c910d5996
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: fe69d4c897491166a632bbc38f466aadfb9a1e63
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="registry-entries-for-data-sources"></a>Записи реестра для источников данных
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включается в операционной системе Windows. ODBC следует устанавливать только явно на более ранних версиях Windows.  
  
 Установщик DLL сохраняет сведения о каждом источнике данных. В Microsoft Windows NT, Windows 2000 и Microsoft Windows 95/98 эти сведения хранятся в подразделах в одном из следующих двух разделов в реестре:  
  
 HKEY_LOCAL_MACHINE  
  
 ПРОГРАММНОЕ ОБЕСПЕЧЕНИЕ  
  
 интерфейс ODBC  
  
 ODBC.ini  
  
 HKEY_CURRENT_USER  
  
 ПРОГРАММНОЕ ОБЕСПЕЧЕНИЕ  
  
 интерфейс ODBC  
  
 ODBC.ini  
  
 Ключ используется зависит от источника данных *системного источника данных,* доступный для всех пользователей или *источника данных* доступного только для текущего пользователя. Системные источники данных хранятся в дереве HKEY_LOCAL_MACHINE, и пользовательские источники данных хранятся в дереве HKEY_CURRENT_USER. Во всех прочих отношениях идентичны системные источники данных и источники данных пользователя.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Подраздел источников данных ODBC](../../../odbc/reference/install/odbc-data-sources-subkey.md)  
  
-   [Подразделы спецификации источника данных](../../../odbc/reference/install/data-source-specification-subkeys.md)  
  
-   [Подраздел по умолчанию](../../../odbc/reference/install/default-subkey.md)  
  
-   [Подраздел ODBC](../../../odbc/reference/install/odbc-subkey.md)
