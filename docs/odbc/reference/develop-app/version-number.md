---
title: Номер версии | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 331b60b31c49a203da5f25c4481a604132fbb0e8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079554"
---
# <a name="version-number"></a>Номер версии
Существует несколько версий ODBC, каждый из которых имеет различные функции. Приложение определяет версию ODBC, которую диспетчер драйверов и конкретный драйвер поддерживает, вызывая **SQLGetInfo** с параметрами SQL_ODBC_VER и SQL_DRIVER_ODBC_VER.
