---
title: Получение указателей дескрипторов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: 936f983f-c7e9-43f3-97ea-dd4b1bbf4654
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8bfa0b36ecca3af655efde84c3ce3f22ab0c1f88
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086310"
---
# <a name="obtaining-descriptor-handles"></a>Получение указателей дескрипторов
Приложение получает дескриптор любые явно выделенные дескрипторы в виде выходного аргумент вызова **SQLAllocHandle**. Дескриптор дескриптор неявно выделенные получается путем вызова **SQLGetStmtAttr**.
