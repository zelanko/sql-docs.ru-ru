---
title: Компоненты установки | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
- ODBC [ODBC], component installation
ms.assetid: 9de15ca0-fe6a-4634-8709-a928d3c9cc73
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a883377a17aa9e0c3426b4805263616375ea6215
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53208783"
---
# <a name="installation-components"></a>Компоненты установки
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включена в операционную систему Windows. ODBC следует только явным образом установить в более ранних версиях Windows.  
  
 Начнется процесс установки, когда пользователь запускает программу установки. Программа установки работает в сочетании с *библиотека DLL установщика* и *DLL-файлов установки драйвера* для каждого драйвера. Программа установки и библиотека DLL установщика используйте аргументы в **SQLInstallDriverEx** и **SQLInstallTranslatorEx** функции, чтобы определить, какие файлы для копирования или удаления для каждого компонента. Ниже показана связь между этими компонентами установки.  
  
 ![Связь между компонентами установки](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]
>  Файл Odbc.inf, который использовался в ODBC 2. *x* для описания файлы, необходимые для каждого ODBC компонент не используется в ODBC 3 *.x*. Драйверы, поставляемые ODBC 3 *.x* компоненты не нужно создавать файл Odbc.inf. Удаление **SQLInstallDriver** и **SQLInstallODBC**и об использовании **SQLInstallTranslator**, к просмотру Odbc.inf ненужные. Сведения о драйвере, который был в разделах слово Driver Odbc.inf теперь предоставляются в *lpszDriver* аргумента в **SQLInstallDriverEx**. Сведения перевода, используются в [ODBC Translator] и разделах спецификации Translator Odbc.inf теперь предоставляются в *lpszTranslator* аргумент **SQLInstallTranslatorEx**. Эти изменения разрешите установщику ODBC можно более пригодным для переноса на другие платформы.  
  
 Дополнительные сведения об этих компонентах см. в следующих разделах, в конце этого раздела.  
  
-   [Программа установки](../../../odbc/reference/install/setup-program.md)  
  
-   [Библиотека DLL установщика](../../../odbc/reference/install/installer-dll.md)  
  
-   [Библиотека DLL программы установки драйвера](../../../odbc/reference/install/driver-setup-dll.md)
