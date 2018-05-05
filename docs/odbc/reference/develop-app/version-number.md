---
title: Номер версии | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- version number supported [ODBC]
- interoperability [ODBC], version number supported
ms.assetid: 6eccacdf-b837-4b66-bd48-ba31771acecb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 06f5293f7c4a2f89560970303f599c4759c82bd3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="version-number"></a>Номер версии
Существует несколько версий ODBC, каждый с разными функциями. Приложение определяет, какая версия ODBC Driver Manager и драйвер поддерживает путем вызова **SQLGetInfo** параметры SQL_ODBC_VER и SQL_DRIVER_ODBC_VER.
