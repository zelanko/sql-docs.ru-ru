---
title: Несколько активных заявлений и подключений Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], multiple active statements and connections
- multiple active statements and connections [ODBC]
ms.assetid: a6571356-b23e-4f10-a17b-bce09460b71e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8259967942f47b06c50a9043158f8b3b45c58d7a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302433"
---
# <a name="multiple-active-statements-and-connections"></a>Множественные активные инструкции и подключения
Некоторые драйверы и DBMS ограничивают количество выписок и соединений, которые могут быть активны в одно время. Эти цифры могут быть столь же малы, как один. Для получения дополнительной информации ознакомьтесь с вариантами SQL_MAX_CONCURRENT_ACTIVITIES и SQL_MAX_DRIVER_CONNECTIONS в описании функции [S'LGetInfo,](../../../odbc/reference/syntax/sqlgetinfo-function.md) а также в [обработках и ручках](../../../odbc/reference/develop-app/statement-handles.md) [на подключение.](../../../odbc/reference/develop-app/connection-handles.md)
