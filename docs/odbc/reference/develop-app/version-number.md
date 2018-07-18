---
title: Номер версии | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: 05629fd8d944ed62325a3af5a18d8431c49e1aa2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32917309"
---
# <a name="version-number"></a>Номер версии
Существует несколько версий ODBC, каждый с разными функциями. Приложение определяет, какая версия ODBC Driver Manager и драйвер поддерживает путем вызова **SQLGetInfo** параметры SQL_ODBC_VER и SQL_DRIVER_ODBC_VER.
