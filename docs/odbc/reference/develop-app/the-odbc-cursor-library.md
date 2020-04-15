---
title: Библиотека ODBC Cursor (англ.) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b243e8ae2dc931830a249d4392da308e68722cdf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300054"
---
# <a name="the-odbc-cursor-library"></a>Библиотека курсоров ODBC
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Блок и прокрутки курсоры очень полезные дополнения ко многим приложениям. Однако не все драйверы поддерживают блок и прокрутки курсоров. То же самое относится и к позиционированным заявлениям об обновлении и удалении, а также к **S'LSetPos,** которые обсуждаются в области обновления данных. Таким образом, компонент ODBC SDK Windows, ранее включенный в SDK microsoft Data Access Components (MDAC), включает в себя библиотеку курсоров. Библиотека курсоров, реализует блок, статические курсоры, позиционированные операторы обновления и удаления, а также **S'LSetPos** для любого драйвера, который соответствует уровню соответствия open Group Standard CLI. Библиотека курсоров может быть перераспределена с помощью приложений ODBC; Для получения дополнительной информации в SDK можно ознакомиться с данными о лицензионном соглашении в SDK.  
  
 Чтобы использовать библиотеку курсоров, приложение устанавливает атрибут SQL_ATTR_ODBC_CURSORS соединения, прежде чем он подключается к источнику данных. Для получения дополнительной информации о библиотеке курсора, [см.](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md)
