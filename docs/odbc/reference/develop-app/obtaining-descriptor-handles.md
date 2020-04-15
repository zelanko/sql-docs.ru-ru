---
title: Получение дескрипторных ручек (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c17b693080c2727d2ee788b74f247d86d7a3cb27
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302349"
---
# <a name="obtaining-descriptor-handles"></a>Получение указателей дескрипторов
Приложение получает ручку любого явно выделенного дескриптора в качестве выходного аргумента вызова в **S'LAllocHandle.** Ручка неявно выделенного дескриптора получена по телефону **S'LGetStmtAttr.**
