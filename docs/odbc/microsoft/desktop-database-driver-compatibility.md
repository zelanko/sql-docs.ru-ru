---
title: Совместимость драйверов для настольных баз данных (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], Unicode
- Unicode [ODBC], desktop database drivers
- ODBC desktop database drivers [ODBC], Unicode
- backward compatibility [ODBC], Unicode
- desktop database drivers [ODBC], Unicode
- Jet-based ODBC drivers [ODBC], Unicode
ms.assetid: dd695638-1a0b-4e27-8a6a-9510ebb5a5ee
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 89eea7ab112eaefdc73c7cbc72ee3555797c7efd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303525"
---
# <a name="desktop-database-driver-compatibility"></a>Совместимость драйверов для баз данных на настольном компьютере
Unicode — это метод кодирования программных символов, который рассматривает все символы как имеющие фиксированную ширину в два байта. Этот метод используется в качестве альтернативы кодированию символов Windows ANSI, которое, поскольку представляет символы в одном байте, ограничено 256 символами. Поскольку Unicode может представлять более 65 000 символов, он вмещает многие языки, символы которых не представлены в кодировании ANSI.  
  
 Менеджер драйверов ODBC 3.5 (или позже) включен в систему Unicode. Это влияет на две основные области: вызовы функций и типы строк данных. Карты Driver Manager функционируют строки аргументов и строки данных, как того требует приложение и драйвер, оба из которых могут быть либо Unicode с поддержкой или ANSI-включен.  
  
 Менеджер драйверов ODBC 3.5 (или позже) поддерживает использование драйвера Unicode как с помощью приложения Unicode, так и с помощью приложения ANSI. Он также поддерживает использование драйвера ANSI с помощью приложения ANSI. Менеджер драйверов предоставляет ограниченное отображение Unicode-ANSI для приложения Unicode, работающего с драйвером ANSI. Это позволяет получить доступ к базам данных Jet 3.5 и поддерживать все существующие типы файлов ISAM.  
  
 Когда приложение ANSI использует драйвер базы данных ODBC Desktop 2.0 и получает доступ к Microsoft Access 4.0 или позже, драйвер предоставляет тип данных как SQL_CHAR, SQL_VARCHAR или SQL_LONGVARCHAR, даже если Jet 4.0 поддерживает широкую версию. Старые версии Jet не поддерживают SQL_WCHAR, SQL_WVARCHAR и SQL_WLONGVARCHAR. Это ограничение также применяется в тех случаях, когда старые форматы используются с Jet 4.0 Database Engine.  
  
 Для получения дополнительной информации о проблемах Unicode с ODBC, [см.](../../odbc/reference/develop-app/unicode.md)
