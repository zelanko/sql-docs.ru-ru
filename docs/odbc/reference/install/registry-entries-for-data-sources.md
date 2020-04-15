---
title: Записи регистрации для источников данных Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c73ea704b091bc37afb1ac42b520304022d929c3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296274"
---
# <a name="registry-entries-for-data-sources"></a>Записи реестра для источников данных
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включен в систему работы Windows. Вы должны только явно установить ODBC на более ранних версиях Windows.  
  
 Установщик DLL поддерживает в реестре информацию о каждом источнике данных. В Microsoft Windows NT/Windows 2000 и Microsoft Windows 95/98 эта информация хранится в подкеях под одним из следующих двух ключей в реестре:  

 ```console
 HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\Odbc.ini  
 ```

 ```console
 HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini
 ```

 Какой ключ используется, зависит от того, является ли источник данных *источником системных данных,* который доступен для всех пользователей, или *источником пользовательских данных,* который доступен только текущему пользователю. Источники системных данных хранятся на HKEY_LOCAL_MACHINE дереве, а источники пользовательских данных — на HKEY_CURRENT_USER дереве. Во всех остальных отношениях источники системных данных и источники пользовательских данных идентичны.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Подраздел источников данных ODBC](../../../odbc/reference/install/odbc-data-sources-subkey.md)  
  
-   [Подразделы спецификации источника данных](../../../odbc/reference/install/data-source-specification-subkeys.md)  
  
-   [Подраздел по умолчанию](../../../odbc/reference/install/default-subkey.md)  
  
-   [Подраздел ODBC](../../../odbc/reference/install/odbc-subkey.md)
