---
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
ms.openlocfilehash: 155ef4951abddc7a73d9d4abfbc45248f33d653c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306311"
---
# <a name="bound-descriptor-records"></a>Связанные записи дескриптора
Когда приложение задает SQL_DESC_DATA_PTR поле записи дескриптора, чтобы оно больше не содержало значение null, считается, что запись *привязана*.  
  
 Если дескриптор является APD, то каждая привязанная запись образует связанный параметр. Для входных параметров приложение должно привязать параметр для каждого маркера динамического параметра в инструкции SQL перед выполнением инструкции. Для выходных параметров приложению не требуется привязывать параметр.  
  
 Если дескриптор является АРД, описывающим строку данных базы данных, каждая связанная запись образует связанный столбец.
