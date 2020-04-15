---
title: Номер версии Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- version number supported [ODBC]
- interoperability [ODBC], version number supported
ms.assetid: 6eccacdf-b837-4b66-bd48-ba31771acecb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 37b7924380b9e9beb60792b50436eaa13a503c76
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306722"
---
# <a name="version-number"></a>Номер версии
Есть несколько версий ODBC, каждая из которых имеет различные функции. Приложение определяет, какая версия ODBC является менеджером драйвера и конкретной поддержкой драйвера, позвонив в **s'LGetInfo** с SQL_ODBC_VER и SQL_DRIVER_ODBC_VER опций.
