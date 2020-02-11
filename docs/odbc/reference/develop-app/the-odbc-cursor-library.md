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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114071"
---
# <a name="the-odbc-cursor-library"></a>Библиотека курсоров ODBC
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Блочные и прокручиваемые курсоры являются очень полезными дополнениями для многих приложений. Однако не все драйверы поддерживают блочные и прокручиваемые курсоры. Это справедливо и для позиционированных инструкций UPDATE и DELETE и **SQLSetPos**, которые обсуждаются в разделе Обновление данных. Таким образом, компонент ODBC Windows SDK, ранее включенный в пакет SDK для компонентов доступа к данным Microsoft (MDAC), включает библиотеку курсоров. Библиотека курсоров реализует блок, статические курсоры, позиционированные обновления и инструкции DELETE, а также функцию **SQLSetPos** для любого драйвера, удовлетворяющего стандартному уровню соответствия CLI для группы. Библиотеку курсоров можно распространять вместе с приложениями ODBC. Дополнительные сведения см. в соглашении о лицензировании в пакете SDK.  
  
 Чтобы использовать библиотеку курсоров, приложение задает SQL_ATTR_ODBC_CURSORS атрибут подключения перед подключением к источнику данных. Дополнительные сведения о библиотеке курсоров см. в [приложении F: Библиотека курсоров ODBC](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md).
