---
title: Записи реестра для компонентов ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC]
- installing ODBC components [ODBC], registry entries
- registry entries for components [ODBC]
- subkeys [ODBC], for components
- registry entries for components [ODBC], about registry entries
ms.assetid: c90aa8a4-6ece-48de-901c-17d23739a9ff
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d0a654b70fb93020bbb0dcfde159b4884cb15c0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47651483"
---
# <a name="registry-entries-for-odbc-components"></a>Записи реестра для компонентов ODBC
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включена в операционную систему Windows. ODBC следует только явным образом установить в более ранних версиях Windows.  
  
 Библиотека DLL установщика сохраняет сведения в реестре о каждого установленного компонента ODBC. На компьютерах под управлением Microsoft Windows NT и Microsoft Windows 95/98 эти сведения хранятся в подразделах в следующем разделе реестра:  
  
 HKEY_LOCAL_MACHINE  
  
 ПРОГРАММНОЕ ОБЕСПЕЧЕНИЕ  
  
 интерфейс ODBC  
  
 Odbcinst.ini  
  
 Поскольку Odbcinst.ini подраздела дерева HKEY_LOCAL_MACHINE, сведения о компонентах ODBC доступен для всех пользователей компьютера.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Подраздел Core ODBC](../../../odbc/reference/install/odbc-core-subkey.md)  
  
-   [Подраздел драйвера ODBC](../../../odbc/reference/install/odbc-drivers-subkey.md)  
  
-   [Подразделы спецификаций драйверов](../../../odbc/reference/install/driver-specification-subkeys.md)  
  
-   [Подраздел драйвера по умолчанию](../../../odbc/reference/install/default-driver-subkey.md)  
  
-   [Подраздел ODBC-преобразователей](../../../odbc/reference/install/odbc-translators-subkey.md)  
  
-   [Подразделы спецификаций преобразователей](../../../odbc/reference/install/translator-specification-subkeys.md)
