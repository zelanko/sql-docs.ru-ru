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
ms.topic: conceptual
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
ms.openlocfilehash: c225109657906459d86ab5d19e441158c16ca57d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
