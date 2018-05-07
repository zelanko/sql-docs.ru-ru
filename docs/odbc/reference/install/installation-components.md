---
title: Компоненты установки | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
- ODBC [ODBC], component installation
ms.assetid: 9de15ca0-fe6a-4634-8709-a928d3c9cc73
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c5fe2538d1567630121f05a4798583099de7200
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="installation-components"></a>Компоненты установки
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включается в операционной системе Windows. ODBC следует устанавливать только явно на более ранних версиях Windows.  
  
 Когда пользователь запускает программу установки, начинается процесс установки. Программа установки работает в сочетании с *установщика DLL* и *DLL-файлов установки драйвера* для каждого драйвера. Программа установки и программа установки DLL использовать аргументы в **SQLInstallDriverEx** и **SQLInstallTranslatorEx** функции, чтобы определить, какие файлы для копирования или удаления для каждого компонента. Ниже показана связь между этими компонентами установки.  
  
 ![Связь между компонентами установки](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]  
>  Файл Odbc.inf, который использовался в ODBC 2. *x* компонент не используется для описания файлов, необходимых для каждого ODBC в ODBC 3 *.x*. Драйверы, поставляемые ODBC 3 *.x* компоненты не нужно создать файл Odbc.inf. Удаление **SQLInstallDriver** и **SQLInstallODBC**и об устаревании **SQLInstallTranslator**, к просмотру Odbc.inf ненужные. Сведений о драйвере, используемой в разделы ключевое слово Driver Odbc.inf теперь предоставляется в *lpszDriver* аргумент в **SQLInstallDriverEx**. Транслятор сведения, содержавшиеся в [переводчик ODBC] и разделах спецификации переводчик Odbc.inf теперь предоставляется в *lpszTranslator* аргумент **SQLInstallTranslatorEx**. Эти изменения разрешите установщику ODBC можно более переносить на другие платформы.  
  
 Дополнительные сведения об этих компонентах см. в следующих разделах, в конце этого раздела.  
  
-   [Программа установки](../../../odbc/reference/install/setup-program.md)  
  
-   [Библиотека DLL установщика](../../../odbc/reference/install/installer-dll.md)  
  
-   [Библиотека DLL программы установки драйвера](../../../odbc/reference/install/driver-setup-dll.md)
