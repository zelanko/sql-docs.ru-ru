---
title: Записи реестра для источников данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC]
- data sources [ODBC], registry entries
- registry entries for data sources [ODBC], about registry entries
- data sources [ODBC], configuring
- registry entries for data sources [ODBC]
ms.assetid: 78aaa3d3-d081-4550-80e3-720c910d5996
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0b9d101395a3276f92f3ccf49e36effc65420f7b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093879"
---
# <a name="registry-entries-for-data-sources"></a>Записи реестра для источников данных
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включена в операционную систему Windows. ODBC следует только явным образом установить в более ранних версиях Windows.  
  
 Библиотека DLL установщика сохраняет сведения в реестре о каждом источнике данных. В Microsoft Windows NT или Windows 2000 и Microsoft Windows 95/98 эти сведения хранятся в подразделах в одном из следующих двух разделов в реестре:  
  
 HKEY_LOCAL_MACHINE  
  
 ПРОГРАММНОЕ ОБЕСПЕЧЕНИЕ  
  
 интерфейс ODBC  
  
 ODBC.ini  
  
 HKEY_CURRENT_USER  
  
 ПРОГРАММНОЕ ОБЕСПЕЧЕНИЕ  
  
 интерфейс ODBC  
  
 ODBC.ini  
  
 Какой ключ используется зависит от того, является ли источник данных *системный источник данных,* доступного для всех пользователей или *источника данных,* доступного только для текущего пользователя. Системные источники данных хранятся в дереве HKEY_LOCAL_MACHINE и пользовательских источников данных хранятся в дереве HKEY_CURRENT_USER. Во всех прочих отношениях идентичны системные источники данных и пользовательских источников данных.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Подраздел источников данных ODBC](../../../odbc/reference/install/odbc-data-sources-subkey.md)  
  
-   [Подразделы спецификации источника данных](../../../odbc/reference/install/data-source-specification-subkeys.md)  
  
-   [Подраздел по умолчанию](../../../odbc/reference/install/default-subkey.md)  
  
-   [Подраздел ODBC](../../../odbc/reference/install/odbc-subkey.md)
