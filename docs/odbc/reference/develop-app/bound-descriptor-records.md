---
description: Связанные записи дескриптора
title: Записи дескрипторов привязки | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- bound descriptor records [ODBC]
- descriptors [ODBC], bound descriptor records
ms.assetid: 55d09344-6682-40f6-b634-036b134ff650
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fcf88374967b5a9d8426d16c9e92c06e4eef32cb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476806"
---
# <a name="bound-descriptor-records"></a>Связанные записи дескриптора
Когда приложение задает SQL_DESC_DATA_PTR поле записи дескриптора, чтобы оно больше не содержало значение null, считается, что запись *привязана*.  
  
 Если дескриптор является APD, то каждая привязанная запись образует связанный параметр. Для входных параметров приложение должно привязать параметр для каждого маркера динамического параметра в инструкции SQL перед выполнением инструкции. Для выходных параметров приложению не требуется привязывать параметр.  
  
 Если дескриптор является АРД, описывающим строку данных базы данных, каждая связанная запись образует связанный столбец.
