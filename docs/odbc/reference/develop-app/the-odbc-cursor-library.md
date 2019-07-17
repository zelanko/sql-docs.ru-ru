---
title: Библиотека курсоров ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], about cursor library
- ODBC cursor library [ODBC]
- cursor library [ODBC], about cursor library
- scrollable cursors [ODBC]
- cursors [ODBC], cursor library
- block cursors [ODBC]
ms.assetid: 32fb7df0-953a-4f68-b041-7d2852e45d0f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a896a5bb41c5530c65573fa22c418199a043f8fa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114071"
---
# <a name="the-odbc-cursor-library"></a>Библиотека курсоров ODBC
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 Блок и Прокручиваемые курсоры являются очень полезных дополнений к нескольким приложениям. Однако не все драйверы поддерживают блока и Прокручиваемые курсоры. Имеет значение true, если позиционированные обновления и удаления и **SQLSetPos**, которые рассматриваются в обновление данных. Таким образом компонент ODBC пакета SDK для Windows, ранее включенных в Microsoft данных Access Components (MDAC) пакета SDK, включает в себя библиотеку курсоров. Библиотека курсоров реализует блок, статические курсоры, инструкций позиционированного обновления и удаления, и **SQLSetPos** для любой драйвер, который соответствует уровню соответствия откройте группу "стандартный" CLI. Библиотека курсоров, которые могут распространяться с приложениями ODBC; см. в разделе соглашение о лицензировании в пакете SDK, Дополнительные сведения.  
  
 Чтобы использовать библиотеку курсоров, приложение устанавливает атрибут соединения SQL_ATTR_ODBC_CURSORS до подключения к источнику данных. Дополнительные сведения о библиотеке курсоров см. в разделе [приложение F: Библиотека курсоров ODBC](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md).
