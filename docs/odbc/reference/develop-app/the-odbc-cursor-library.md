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
manager: craigg
ms.openlocfilehash: a85868cf22fa6d385c3bf75261e0f1cd54e4e1d0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149083"
---
# <a name="the-odbc-cursor-library"></a>Библиотека курсоров ODBC
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 Блок и Прокручиваемые курсоры являются очень полезных дополнений к нескольким приложениям. Однако не все драйверы поддерживают блока и Прокручиваемые курсоры. Имеет значение true, если позиционированные обновления и удаления и **SQLSetPos**, которые рассматриваются в обновление данных. Таким образом компонент ODBC пакета SDK для Windows, ранее включенных в Microsoft данных Access Components (MDAC) пакета SDK, включает в себя библиотеку курсоров. Библиотека курсоров реализует блок, статические курсоры, инструкций позиционированного обновления и удаления, и **SQLSetPos** для любой драйвер, который соответствует уровню соответствия откройте группу "стандартный" CLI. Библиотека курсоров, которые могут распространяться с приложениями ODBC; см. в разделе соглашение о лицензировании в пакете SDK, Дополнительные сведения.  
  
 Чтобы использовать библиотеку курсоров, приложение устанавливает атрибут соединения SQL_ATTR_ODBC_CURSORS до подключения к источнику данных. Дополнительные сведения о библиотеке курсоров см. в разделе [приложение F: Библиотека курсоров ODBC](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md).
