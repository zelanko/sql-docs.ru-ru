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
ms.openlocfilehash: 1fe76ba3926f2883e2518e255eddf0d567134f4d
ms.sourcegitcommit: 594cee116fa4ee321e1f5e5206f4a94d408f1576
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/23/2019
ms.locfileid: "70009355"
---
# <a name="registry-entries-for-data-sources"></a>Записи реестра для источников данных
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC входит в операционную систему Windows. Следует явно устанавливать ODBC только в более ранних версиях Windows.  
  
 Библиотека DLL установщика хранит сведения о каждом источнике данных в реестре. В Microsoft Windows NT, Windows 2000 и Microsoft Windows 95/98 эта информация хранится в подразделах одного из следующих двух разделов реестра:  

 ```console
 HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\Odbc.ini  
 ```

 ```console
 HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini
 ```

 Используемый ключ зависит от того, является ли источник данных системным *источником данных,* доступным для всех пользователей, или *источником данных пользователя,* доступным только для текущего пользователя. Системные источники данных хранятся в дереве HKEY_LOCAL_MACHINE, а пользовательские источники данных хранятся в дереве HKEY_CURRENT_USER. Во всех прочих отношениях Системные источники данных и пользовательские источники данных идентичны.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Подраздел источников данных ODBC](../../../odbc/reference/install/odbc-data-sources-subkey.md)  
  
-   [Подразделы спецификации источника данных](../../../odbc/reference/install/data-source-specification-subkeys.md)  
  
-   [Подраздел по умолчанию](../../../odbc/reference/install/default-subkey.md)  
  
-   [Подраздел ODBC](../../../odbc/reference/install/odbc-subkey.md)
