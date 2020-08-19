---
description: Номер версии
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 86da481ef7854bb9878c2bac565ef2797b61f5ab
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421428"
---
# <a name="version-number"></a>Номер версии
Существует несколько версий ODBC, каждый из которых имеет различные функции. Приложение определяет версию ODBC, которую диспетчер драйверов и конкретный драйвер поддерживает, вызывая **SQLGetInfo** с параметрами SQL_ODBC_VER и SQL_DRIVER_ODBC_VER.
