---
title: "О совместимости драйверов для настольных баз данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compatibility [ODBC], Unicode
- Unicode [ODBC], desktop database drivers
- ODBC desktop database drivers [ODBC], Unicode
- backward compatibility [ODBC], Unicode
- desktop database drivers [ODBC], Unicode
- Jet-based ODBC drivers [ODBC], Unicode
ms.assetid: dd695638-1a0b-4e27-8a6a-9510ebb5a5ee
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 34b9221b117819988e44196cee0f04578e85d436
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="desktop-database-driver-compatibility"></a>О совместимости драйверов для настольных баз данных
Юникод является метод программного обеспечения кодировки символов, считает все символы с фиксированной ширины в два байта. Этот метод используется в качестве альтернативы для кодировки Windows ANSI, так как он представляет символы в один байт, это ограничение в 256 символов. Поскольку Юникода может представлять более 65 000 символов, она предусматривает многих языков, символы которых не представлены в кодировке ANSI.  
  
 Диспетчер драйверов ODBC 3.5 (или более поздней версии) поддерживает Юникод. Это влияет на две основные области: вызовами функции и строковые типы данных. Диспетчер драйверов maps строка аргументы функций и строковые данные, требуемые для приложений и драйверов, из которых может быть поддержкой ANSI или Юникод.  
  
 Диспетчер драйверов ODBC 3.5 (или более поздней версии) поддерживает использование драйвера Юникода с помощью приложения с поддержкой Юникода и приложение ANSI. Оно также поддерживает использование драйвера ANSI с приложением ANSI. Диспетчер драйверов предоставляет ограниченный сопоставление Unicode-ANSI для приложения с поддержкой Юникода, работе с драйвером ANSI. Это обеспечивает доступ к базы данных Jet 3.5 и поддержка существующих ISAM файлов всех типов.  
  
 Когда приложение ANSI, использует базы данных драйвера ODBC Desktop 4.0 и обращается к Microsoft Access 4.0 или более поздней версии, драйвер предоставляет тип данных как SQL_CHAR, SQL_VARCHAR или SQL_LONGVARCHAR, несмотря на то, что Jet 4.0 поддерживает широкую версию. SQL_WCHAR, SQL_WVARCHAR и SQL_WLONGVARCHAR не поддерживают более старых версий Jet. Это ограничение также применяется в случаях, где используются старые форматы с ядром базы данных Jet 4.0.  
  
 Дополнительные сведения, касающиеся Юникод проблемы с ODBC см. в разделе [Юникода](../../odbc/reference/develop-app/unicode.md) в вопросы программирования.

