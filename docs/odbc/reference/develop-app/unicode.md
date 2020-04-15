---
title: Unicode Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC]
- Unicode [ODBC], about Unicode
ms.assetid: 113e1c9a-8333-4805-86f2-e4b57ab816a5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9824e76cebabb6f5f84505292801a0094e359f0f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302451"
---
# <a name="unicode"></a>Юникод
Unicode определяет кодирование символов на многих языках.  
  
 Для получения дополнительной информации о [The Unicode Consortium](https://www.unicode.org)стандарте Unicode см.  
  
 Unicode определяет универсальный набор символов. Страница кода Windows ANSI определяет набор символов, обычно содержащий символы для одного языка. Возможно, будет сложнее написать приложение, которое требуется для использования различных страниц кода.  
  
 Unicode не требует страницы кода. Каждая точка кода отображается на одном символе на одном языке.  
  
 В настоящее время единственным кодированием Unicode, которое поддерживает ODBC, является UCS-2, который использует 16-битную цельную (фиксированную длину) для представления символа. Unicode позволяет приложениям работать на разных языках.  
  
 Менеджер драйверов ODBC 3.5 (или выше) включен в систему Unicode. Это влияет на две основные области: вызовы функций и типы строк данных. Карты Driver Manager функционируют строки аргументов и строки данных, как того требует приложение и драйвер, оба из которых могут быть либо Unicode с поддержкой или ANSI-включен. Эти две области подробно обсуждаются в разделах, [Unicode Function Аргументы](../../../odbc/reference/develop-app/unicode-function-arguments.md) и [Unicode данных](../../../odbc/reference/develop-app/unicode-data.md).  
  
 Менеджер драйверов ODBC 3.5 (или выше) поддерживает использование драйвера Unicode как с помощью приложения Unicode, так и приложения ANSI. Он также поддерживает использование драйвера ANSI с помощью приложения ANSI. Менеджер драйверов предоставляет ограниченное отображение Unicode-ANSI для приложения Unicode, работающего с драйвером ANSI.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Аргументы функции Юникода](../../../odbc/reference/develop-app/unicode-function-arguments.md)  
  
-   [Данные в Юникоде](../../../odbc/reference/develop-app/unicode-data.md)
