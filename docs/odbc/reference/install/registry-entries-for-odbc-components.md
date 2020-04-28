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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bead63f11b253342cd444e1d5bd0697ee00cfbc1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296184"
---
# <a name="registry-entries-for-odbc-components"></a>Записи реестра для компонентов ODBC
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC входит в операционную систему Windows. Следует явно устанавливать ODBC только в более ранних версиях Windows.  
  
 Библиотека DLL установщика хранит сведения о каждом установленном компоненте ODBC в реестре. На компьютерах под управлением Microsoft Windows NT и Microsoft Windows 95/98 эта информация хранится в подразделах в следующем разделе реестра:  

 ```console
 HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\Odbcinst.ini
 ```

 Так как Odbcinst. ini является подразделом дерева HKEY_LOCAL_MACHINE, сведения о компонентах ODBC доступны для всех пользователей компьютера.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Подраздел Core ODBC](../../../odbc/reference/install/odbc-core-subkey.md)  
  
-   [Подраздел драйвера ODBC](../../../odbc/reference/install/odbc-drivers-subkey.md)  
  
-   [Подразделы спецификаций драйверов](../../../odbc/reference/install/driver-specification-subkeys.md)  
  
-   [Подраздел драйвера по умолчанию](../../../odbc/reference/install/default-driver-subkey.md)  
  
-   [Подраздел ODBC-преобразователей](../../../odbc/reference/install/odbc-translators-subkey.md)  
  
-   [Подразделы спецификаций преобразователей](../../../odbc/reference/install/translator-specification-subkeys.md)
