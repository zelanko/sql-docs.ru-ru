---
title: Связанные записи дескриптора | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6f7d21a1166868603f9389ab4ef5c5b3448b0312
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199531"
---
# <a name="bound-descriptor-records"></a>Связанные записи дескриптора
Когда приложение задает поле запись дескриптора SQL_DESC_DATA_PTR, таким образом, чтобы он больше не содержит значение null, запись считается *привязан*.  
  
 Если дескриптор является APD, каждой присоединенной записи составляет привязанного параметра. Для входных параметров приложения необходимо выполнить привязку параметра для каждого маркера параметра динамического в инструкцию SQL перед выполнением инструкции. Для выходных параметров приложение не требуется выполнить привязку параметра.  
  
 Если Отменить, который описывает строку данных в базе данных, используется дескриптор каждой присоединенной записи составляет связанного столбца.
